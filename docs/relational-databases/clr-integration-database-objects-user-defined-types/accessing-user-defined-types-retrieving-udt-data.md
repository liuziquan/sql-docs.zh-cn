---
title: 检索 UDT 数据 |微软文档
description: 本文介绍如何在 SQL Server 数据库中访问 UDT。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SqlDataReader object
- ADO.NET [CLR integration]
- binding UDTs [CLR integration]
- UDTs [CLR integration], ADO.NET
- assemblies [CLR integration], user-defined types
- query parameters [CLR integration]
- user-defined types [CLR integration], ADO.NET
- bytes [CLR integration]
ms.assetid: 6a98ac8c-0e69-4c03-83a4-2062cb782049
author: rothja
ms.author: jroth
ms.openlocfilehash: e3d14c6d24d6db5d27b12bcc3f28c1b6ba383442
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488216"
---
# <a name="accessing-user-defined-types---retrieving-udt-data"></a>访问用户定义类型 - 检索 UDT 数据
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  若要在客户端上创建用户定义类型 (UDT)，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中作为 UDT 注册的程序集必须可供客户端应用程序使用。 UDT 程序集可位于该应用程序的相同目录中，也可以位于全局程序集缓存 (GAC) 中。 还可以在项目中设置对该程序集的引用。  
  
## <a name="requirements-for-using-udts-in-adonet"></a>在 ADO.NET 中使用 UDT 的要求  
 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中加载的程序集和客户端上的程序集必须兼容，以便在该客户端上创建 UDT。 对于使用**本机**序列化格式定义的 UDT，程序集必须在结构上兼容。 对于使用**用户定义**格式定义的程序集，程序集必须在客户端上可用。  
  
 您无需在客户端上复制 UDT 程序集即可检索表中 UDT 列的原始数据。  
  
> [!NOTE]  
>  如果 UDT 版本不匹配或其他问题 **，SqlClient**可能无法加载 UDT。 在这种情况下，请使用常规故障排除机制确定调用应用程序无法找到包含 UDT 的程序集的原因。 有关详细信息，请参阅 .NET Framework 文档中的“使用托管调试助手诊断错误”主题。  
  
## <a name="accessing-udts-with-a-sqldatareader"></a>通过 SqlDataReader 访问 UDT  
 **System.Data.SqlClient.SqlDataReader**可以从客户端代码中检索包含 UDT 列的结果集，该列作为对象的实例公开。  
  
### <a name="example"></a>示例  
 此示例演示如何使用**Main**方法创建新的**SqlDataReader**对象。 下面的操作是在代码示例中执行的：  
  
1.  Main 方法创建新的**SqlDataReader**对象，并从"点"表中检索值，该表具有名为 Point 的 UDT 列。  
  
2.  该 Point UDT 公开定义为整数的 X 和 Y 坐标。  
  
3.  UDT 定义**距离**方法和**获取距离XY**方法。  
  
4.  示例代码检索主键列和 UDT 列的值，以便显示 UDT 的功能。  
  
5.  示例代码调用**点.距离**和**点.获取距离XY**方法。  
  
6.  结果将显示在控制台窗口中。  
  
> [!NOTE]  
>  应用程序必须已具有对 UDT 程序集的引用。  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
  
Module ReadPoints  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Retrieve the value of the UDT  
                Dim pnt As Point = CType(rdr(1), Point)  
  
             ' You can also use GetSqlValue and GetValue  
             ' Dim pnt As Point = CType(rdr.GetSqlValue(1), Point)  
             ' Dim pnt As Point = CType(rdr.GetValue(1), Point)  
  
                ' Print values  
                Console.WriteLine( _  
                 "ID={0} Point={1} X={2} Y={3} DistanceFromXY={4} Distance={5}", _  
                  id, pnt, pnt.X, pnt.Y, pnt.DistanceFromXY(1, 9), pnt.Distance())  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
         & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
  
namespace Microsoft.Samples.SqlServer  
{  
class ReadPoints  
{  
static void Main()  
{  
  string connectionString = GetConnectionString();  
  using (SqlConnection cnn = new SqlConnection(connectionString))  
  {  
    cnn.Open();  
    SqlCommand cmd = new SqlCommand(  
       "SELECT ID, Pnt FROM dbo.Points", cnn);  
    SqlDataReader rdr = cmd.ExecuteReader();  
  
    while (rdr.Read())  
    {  
      // Retrieve the value of the Primary Key column  
      int id = rdr.GetInt32(0);  
  
        // Retrieve the value of the UDT  
        Point pnt = (Point)rdr[1];  
  
        // You can also use GetSqlValue and GetValue  
        // Point pnt = (Point)rdr.GetSqlValue(1);  
        // Point pnt = (Point)rdr.GetValue(1);  
  
        Console.WriteLine(  
        "ID={0} Point={1} X={2} Y={3} DistanceFromXY={4} Distance={5}",   
        id, pnt, pnt.X, pnt.Y, pnt.DistanceFromXY(1, 9), pnt.Distance());  
    }  
  rdr.Close();  
  Console.WriteLine("done");  
  }  
  static private string GetConnectionString()  
  {  
    // To avoid storing the connection string in your code,   
    // you can retrieve it from a configuration file.  
    return "Data Source=(local);Initial Catalog=AdventureWorks;"  
        + "Integrated Security=SSPI";  
  }  
}  
```  
  
## <a name="binding-udts-as-bytes"></a>以字节形式绑定 UDT  
 在某些情况下，您可能希望检索 UDT 列中的原始数据。 本地可能没有可用类型，或者您可能不希望实例化 UDT 实例。 您可以使用**SqlDataReader**的**GetBytes**方法将原始字节读取到字节数组中。 该方法从指定的列偏移量将字节流作为数组从指定缓冲区偏移量开始读入缓冲区。 另一个选项是使用**GetSqlBytes**或**GetSqlBinary**方法之一，并在单个操作中读取所有内容。 无论何种情况，永远不会实例化 UDT 对象，因此，您无需在客户端程序集中设置对 UDT 的引用。  
  
### <a name="example"></a>示例  
 此示例演示如何使用**SqlDataReader**将**Point**数据作为原始字节检索到字节数组中。 该代码使用**System.Text.StringBuilder**将原始字节转换为要显示在控制台窗口中的字符串表示形式。  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Text  
  
Module GetRawBytes  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Retrieve the raw bytes into a byte array  
                Dim buffer(31) As Byte  
                Dim byteCount As Integer = _  
                 CInt(rdr.GetBytes(1, 0, buffer, 0, 31))  
  
                ' Format and print bytes   
                Dim str As New StringBuilder  
                str.AppendFormat("ID={0} Point=", id)  
  
                Dim i As Integer  
                For i = 0 To (byteCount - 1)  
                    str.AppendFormat("{0:x}", buffer(i))  
                Next  
                Console.WriteLine(str.ToString)  
  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Text;  
  
class GetRawBytes  
{  
    static void Main()  
    {  
        string connectionString = GetConnectionString();  
        using (SqlConnection cnn = new SqlConnection(connectionString))  
        {  
            cnn.Open();  
            SqlCommand cmd = new SqlCommand("SELECT ID, Pnt FROM dbo.Points", cnn);  
            SqlDataReader rdr = cmd.ExecuteReader();  
  
            while (rdr.Read())  
            {  
                // Retrieve the value of the Primary Key column  
                int id = rdr.GetInt32(0);  
  
                // Retrieve the raw bytes into a byte array  
                byte[] buffer = new byte[32];  
                long byteCount = rdr.GetBytes(1, 0, buffer, 0, 32);  
  
                // Format and print bytes   
                StringBuilder str = new StringBuilder();  
                str.AppendFormat("ID={0} Point=", id);  
  
                for (int i = 0; i < byteCount; i++)  
                    str.AppendFormat("{0:x}", buffer[i]);  
                Console.WriteLine(str.ToString());  
            }  
            rdr.Close();  
            Console.WriteLine("done");  
        }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
### <a name="example-using-getsqlbytes"></a>使用 GetSqlBytes 的示例  
 此示例演示如何使用**GetSqlBytes**方法在单个操作中检索**点**数据作为原始字节。 代码使用**StringBuilder**将原始字节转换为要在控制台窗口中显示的字符串表示形式。  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Text  
  
Module GetRawBytes  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Use SqlBytes to retrieve raw bytes  
                Dim sb As SqlBytes = rdr.GetSqlBytes(1)  
                Dim byteCount As Long = sb.Length  
  
                ' Format and print bytes   
                Dim str As New StringBuilder  
                str.AppendFormat("ID={0} Point=", id)  
  
                Dim i As Integer  
                For i = 0 To (byteCount - 1)  
                    str.AppendFormat("{0:x}", sb(i))  
                Next  
                Console.WriteLine(str.ToString)  
  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Text;  
  
class GetRawBytes  
{  
    static void Main()  
    {  
         string connectionString = GetConnectionString();  
        using (SqlConnection cnn = new SqlConnection(connectionString))  
        {  
            cnn.Open();  
            SqlCommand cmd = new SqlCommand(  
                "SELECT ID, Pnt FROM dbo.Points", cnn);  
            SqlDataReader rdr = cmd.ExecuteReader();  
  
            while (rdr.Read())  
            {  
                // Retrieve the value of the Primary Key column  
                int id = rdr.GetInt32(0);  
  
                // Use SqlBytes to retrieve raw bytes  
                SqlBytes sb = rdr.GetSqlBytes(1);  
                long byteCount = sb.Length;  
  
                // Format and print bytes   
                StringBuilder str = new StringBuilder();  
                str.AppendFormat("ID={0} Point=", id);  
  
                for (int i = 0; i < byteCount; i++)  
                    str.AppendFormat("{0:x}", sb[i]);  
                Console.WriteLine(str.ToString());  
            }  
            rdr.Close();  
            Console.WriteLine("done");  
        }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
## <a name="working-with-udt-parameters"></a>使用 UDT 参数  
 可以在 ADO.NET 代码中将 UDT 作为输入参数和输出参数使用。  
  
## <a name="using-udts-in-query-parameters"></a>在查询参数中使用 UDT  
 在为**系统**设置**Sql 参数**时，UDT 可用作参数值。 **SqlParameter 对象的** **SqlDbType.Udt**枚举用于指示参数在将**Add**方法调用**参数**集合时是 UDT。 **SqlCommand**对象的**UdtTypeName**属性用于使用数据库指定数据库中 UDT 的完全限定名称 *. schema_name.object_name*语法。 虽然这不是必需的，但使用完全限定名称可以避免代码出现混乱。  
  
> [!NOTE]  
>  UDT 程序集的本地副本必须对客户端项目可用。  
  
### <a name="example"></a>示例  
 此示例中的代码创建**SqlCommand**和**SqlParameter**对象，将数据插入到表中的 UDT 列中。 代码使用**SqlDbType.Udt**枚举来指定数据类型，以及**SqlParameter 对象的** **UdtTypeName**属性来指定数据库中 UDT 的完全限定名称。  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports system.Data  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim ConnectionString As String = GetConnectionString()  
    Dim cnn As New SqlConnection(ConnectionString)  
    Using cnn  
      Dim cmd As SqlCommand = cnn.CreateCommand()  
      cmd.CommandText = "INSERT INTO dbo.Points (Pnt) VALUES (@Point)"  
      cmd.CommandType = CommandType.Text  
  
      Dim param As New SqlParameter("@Point", SqlDbType.Udt)      
      param.UdtTypeName = "TestPoint.dbo.Point"      
      param.Direction = ParameterDirection.Input      
      param.Value = New Point(5, 6)      
      cmd.Parameters.Add(param)  
  
      cnn.Open()  
      cmd.ExecuteNonQuery()  
      Console.WriteLine("done")  
    End Using  
  End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlClient;  
  
class Class1  
{  
static void Main()  
{  
  string ConnectionString = GetConnectionString();  
     using (SqlConnection cnn = new SqlConnection(ConnectionString))  
     {  
       SqlCommand cmd = cnn.CreateCommand();  
       cmd.CommandText =   
         "INSERT INTO dbo.Points (Pnt) VALUES (@Point)";  
       cmd.CommandType = CommandType.Text;  
  
       SqlParameter param = new SqlParameter("@Point", SqlDbType.Udt);       param.UdtTypeName = "TestPoint.dbo.Point";       param.Direction = ParameterDirection.Input;       param.Value = new Point(5, 6);       cmd.Parameters.Add(param);  
  
       cnn.Open();  
       cmd.ExecuteNonQuery();  
       Console.WriteLine("done");  
     }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [在 ADO.NET 中访问用户定义类型](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-in-ado-net.md)  
  
  
