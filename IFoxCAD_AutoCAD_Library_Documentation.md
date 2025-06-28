# IFoxCAD.AutoCAD 库文档

## 概述

IFoxCAD.AutoCAD 是一个基于 .NET 的 AutoCAD 二次开发类库，旨在简化和增强 AutoCAD 应用程序开发。该库提供了丰富的扩展方法、工具类和抽象，使得使用 AutoCAD .NET API 更加直观和高效。

### 库信息
- **包名称**: IFox.CAD.ACAD
- **当前版本**: 0.9.6 (截至 2025年5月)
- **目标框架**:
  - .NET 8.0 (Windows 7.0+)
  - .NET Framework 4.8
- **依赖项**: AutoCAD.NET API
- **许可证**: 开源
- **代码仓库**: https://gitee.com/inspirefunction/ifoxcad

### 项目背景

IFoxCAD 项目起源于雪山飞狐在明经论坛发布的开源库，后经落魄山人整理和重构，形成了现在的 IFoxCAD 类库。项目名称寓意为"I(爱)Fox(狐哥)"，表达对原作者的敬意。该项目发布于 Inspire Function（中文名：跃动方程）组织下。

## 核心功能

### 1. **空间数据结构**
- **四叉树实现**: 高性能的 CAD 实体空间索引
- **碰撞检测**: 先进的实体相交和邻近检测算法
- **空间查询**: 高效的范围查询和最近邻搜索

### 2. **实体管理**
- **数据库扩展**: 简化的数据库操作和事务处理
- **实体扩展**: 丰富的 AutoCAD 实体扩展方法
- **集合工具**: 增强的集合处理和操作功能

### 3. **几何工具**
- **矩形操作**: 全面的矩形/包围盒工具
- **点处理**: 2D/3D 点操作，支持容差处理
- **几何计算**: 向量运算、叉积和空间关系计算

### 4. **编辑器和UI扩展**
- **选择工具**: 增强的实体选择方法
- **用户输入**: 简化的用户交互和输入处理
- **命令行扩展**: 丰富的命令行界面工具

### 5. **数据管理**
- **扩展数据 (XData)**: 简化的扩展数据操作
- **字典操作**: 增强的数据库字典处理
- **编组管理**: 实体分组和组织工具

## 📋 文档目录

### 🚀 [快速开始](#快速开始)
- [安装和配置](#安装和配置)
- [基本使用](#基本使用)
- [Hello World示例](#hello-world示例)

### 🏗️ [核心功能](#核心功能)
- [事务管理 (DBTrans)](#事务管理-dbtrans)
- [数据库扩展 (DatabaseEx)](#数据库扩展-databaseex)
- [文档锁管理](#文档锁管理)
- [DWG文件标记](#dwg文件标记)

### 📐 [实体操作](#实体操作)
- [实体扩展 (EntityEx)](#实体操作-entityex)
- [填充扩展 (HatchEx)](#填充扩展-hatchex)
- [几何计算](#几何计算)
- [实体创建和编辑](#实体创建和编辑)

### 🖱️ [用户交互](#用户交互)
- [编辑器扩展 (EditorEx)](#编辑器扩展-editorex)
- [选择集扩展 (SelectionSetEx)](#选择集扩展-selectionsetex)
- [夹点操作 (JigEx)](#夹点操作-jigex)
- [用户输入处理](#用户输入处理)

### 🔍 [空间数据结构](#空间数据结构)
- [四叉树 (QuadTree)](#四叉树-quadtree)
- [空间查询和索引](#空间查询和索引)
- [性能优化](#性能优化)

### 📁 [文件和数据处理](#文件和数据处理)
- [PE文件分析](#pe文件分析)
- [关联功能](#关联功能)
- [数据转换](#数据转换)

### 🛠️ [工具类和扩展](#工具类和扩展)
- [IFoxCAD.Basal命名空间](#ifoxcadbasal-命名空间)
- [数组和LINQ扩展](#arrayex-数组扩展类)
- [环链表 (LoopList)](#looplist-环链表类)
- [系统API封装](#pinvokeuser32-系统api封装类)
- [调试和验证工具](#debugex-调试工具类)

### ⚠️ [错误处理](#错误处理)
- [CAD错误信息](#cad错误信息处理-errorinfoex)
- [异常处理机制](#异常处理机制)
- [调试和诊断](#调试和诊断)

### 📊 [枚举和常量](#枚举和常量定义)
- [操作模式枚举](#操作模式枚举)
- [系统配置枚举](#系统配置枚举)
- [错误和状态枚举](#错误和状态枚举)
- [UI和交互枚举](#ui和交互枚举)
- [常量和配置项](#常量和配置项)

### 📚 [API参考手册](#api-参考手册)
- [IFoxCAD.Cad命名空间](#ifoxcadcad-命名空间)
- [IFoxCAD.Basal命名空间](#ifoxcadbasal-命名空间-1)
- [快速查找索引](#快速查找索引)

### 💡 [最佳实践](#最佳实践)
- [性能优化建议](#性能优化建议)
- [内存管理](#内存管理)
- [错误处理策略](#错误处理策略)
- [代码组织](#代码组织)

---

## 快速开始

### 安装和配置

### 使用包管理器控制台
```powershell
Install-Package IFox.CAD.ACAD -Version 0.9.6
```

### 使用 .NET CLI
```bash
dotnet add package IFox.CAD.ACAD --version 0.9.6
```

### 使用 PackageReference
```xml
<PackageReference Include="IFox.CAD.ACAD" Version="0.9.6" />
```

### 支持的框架和依赖项

**支持的框架:**
- .NET 8.0 (Windows 7.0+)
- .NET Framework 4.8

**必需依赖项:**
- **AutoCAD.NET**:
  - .NET Framework 4.8 需要版本 >= 20.0.0
  - .NET 8.0 需要版本 >= 25.0.1
- **IndexRange**: >= 1.0.3 (仅 .NET Framework 4.8)

**兼容的 AutoCAD 版本:**
- AutoCAD 2018 及更高版本
- 兼容 ZwCAD 和其他 AutoCAD 兼容平台

## 核心类和命名空间

### IFoxCAD.Cad 命名空间

主要的 CAD 功能命名空间，包含所有核心扩展类和工具。

#### 四叉树系统
- **QuadTree<T>**: 空间索引的根节点控制器
- **QuadTreeNode<T>**: 四叉树结构中的单个节点
- **QuadEntity**: 可在四叉树中索引的实体基类
- **QuadTreeEvn**: 四叉树操作的环境变量和配置

#### 几何类
- **Rect**: 具有空间操作的综合矩形类
- **BulgeVertexWidth**: 多段线顶点数据，包含凸度和宽度信息
- **TolerancePoint2d**: 用于去重的容差点比较

#### 扩展类
- **BaseEx**: 基础扩展工具
- **CollectionEx**: 集合操作扩展
- **DatabaseEx**: 数据库操作扩展
- **DBDictionaryEx**: 字典操作扩展
- **DBObjectEx**: 数据库对象扩展
- **DBTransEx**: 事务扩展
- **EditorEx**: 编辑器和选择扩展

### IFoxCAD.Cad.Assoc 命名空间

关联对象相关功能，用于处理 AutoCAD 的关联性功能和子实体管理。

#### 关联子实体扩展 (AssocPersSubentityIdPEEx)

用于管理和查询AutoCAD实体的子对象关系，提供个性化子实体ID的获取和操作功能。

**主要方法：**

**GetPersSubentityIdPE 方法：**
```csharp
public static AssocPersSubentityIdPE GetPersSubentityIdPE(Entity entity)
```
- **参数：** `entity` - 要查询的实体
- **返回值：** 个性化子对象关系Id实例，如果不存在则返回null
- **用途：** 获取实体的关联性扩展接口

**GetAllSubentityIds 方法：**
```csharp
public static SubentityId[] GetAllSubentityIds(Entity entity, SubentityType subentityType)
```
- **参数：**
  - `entity` - 要查询的实体
  - `subentityType` - 子对象的类型（Face、Edge、Vertex等）
- **返回值：** 所有指定类型的子对象Id数组
- **用途：** 批量获取特定类型的子实体ID

**GetAllSubentities 方法：**
```csharp
public static List<Subentity> GetAllSubentities(Entity entity, SubentityType subentityType)
```
- **参数：**
  - `entity` - 要查询的实体
  - `subentityType` - 子对象的类型
- **返回值：** 所有指定类型的子对象列表
- **用途：** 获取子实体对象的完整信息

**使用示例：**
```csharp
// 获取实体的所有面子实体
var solid = // 获取3D实体
var faceIds = AssocPersSubentityIdPEEx.GetAllSubentityIds(solid, SubentityType.Face);
Console.WriteLine($"实体包含 {faceIds.Length} 个面");

// 获取边子实体
var edgeSubentities = AssocPersSubentityIdPEEx.GetAllSubentities(solid, SubentityType.Edge);
foreach (var edge in edgeSubentities)
{
    // 处理每个边子实体
    Console.WriteLine($"边子实体ID: {edge.SubentityId}");
}

// 检查实体是否支持关联性
var persIdPE = AssocPersSubentityIdPEEx.GetPersSubentityIdPE(solid);
if (persIdPE != null)
{
    Console.WriteLine("实体支持关联性功能");
}
```

#### 关联动作工具 (AssocUtils)

提供AutoCAD关联性系统的高级工具方法，用于创建和管理关联动作。

**主要方法：**

**CreateActionAndActionBodyAndPostToDatabase 方法：**
```csharp
public static ErrorStatus CreateActionAndActionBodyAndPostToDatabase(
    RXClass actionBodyClass,
    ObjectId ownerId,
    out ObjectId actionId,
    out ObjectId actionBodyId)
```
- **参数：**
  - `actionBodyClass` - actionBody的RXClass类型
  - `ownerId` - 拥有者对象ID
  - `actionId` - 输出的动作ID
  - `actionBodyId` - 输出的动作体ID
- **返回值：** 操作结果的错误状态
- **用途：** 替代原生的AssocActionBody.CreateActionAndActionBodyAndPostToDatabase()方法

**使用示例：**
```csharp
// 创建关联动作
using (var tr = new DBTrans())
{
    var ownerObject = // 获取拥有者对象
    var actionBodyClass = // 获取动作体类型

    var result = AssocUtils.CreateActionAndActionBodyAndPostToDatabase(
        actionBodyClass,
        ownerObject.ObjectId,
        out ObjectId actionId,
        out ObjectId actionBodyId);

    if (result == ErrorStatus.OK)
    {
        Console.WriteLine($"关联动作创建成功: Action={actionId}, Body={actionBodyId}");
        tr.Commit();
    }
    else
    {
        Console.WriteLine($"创建失败: {result}");
    }
}
```

**高级应用场景：**
```csharp
// 批量处理实体的子对象
public void ProcessEntitySubentities(Entity entity)
{
    // 获取所有类型的子实体
    var faces = AssocPersSubentityIdPEEx.GetAllSubentities(entity, SubentityType.Face);
    var edges = AssocPersSubentityIdPEEx.GetAllSubentities(entity, SubentityType.Edge);
    var vertices = AssocPersSubentityIdPEEx.GetAllSubentities(entity, SubentityType.Vertex);

    Console.WriteLine($"实体分析结果:");
    Console.WriteLine($"  面数量: {faces.Count}");
    Console.WriteLine($"  边数量: {edges.Count}");
    Console.WriteLine($"  顶点数量: {vertices.Count}");

    // 检查关联性支持
    var persIdPE = AssocPersSubentityIdPEEx.GetPersSubentityIdPE(entity);
    if (persIdPE != null)
    {
        Console.WriteLine("  支持关联性功能");
    }
}
```

### IFoxCAD.Basal 命名空间

基础工具类命名空间，提供通用的扩展方法和工具函数。

**核心工具类：**
- `ArrayEx` - 数组扩展类
- `DebugEx` - 调试工具
- `EnumEx` - 枚举扩展
- `LinqEx` - LINQ 扩展类
- `SystemEx` - 系统扩展
- `RandomEx` - 随机值扩展类

**数据结构：**
- `LoopList<T>` - 环链表
- `LoopListNode<T>` - 环链表节点
- `LoopState` - 控制循环结束
- `ProState` - 控制程序流程

**系统API：**
- `PInvokeUser32` - User32 API 封装
- `WindowsAPI` - Windows API 工具
- `HookType` - 钩子类型枚举
- `WM` - 消息类型

**参数验证：**
- `ArgumentNullEx` - 参数null检查类

## 使用示例

### 基本实体选择
```csharp
using IFoxCAD.Cad;

// 增强的实体选择
var entities = editor.SelectAtPoint(point);
var filteredEntities = editor.SelectByFilter(filter);
```

### 四叉树空间索引
```csharp
// 创建用于空间索引的四叉树
var bounds = new Rect(0, 0, 1000, 1000);
var quadTree = new QuadTree<QuadEntity>(bounds);

// 插入实体
quadTree.Insert(entity);

// 查询区域内的实体
var results = quadTree.Query(queryRect, QuadTreeSelectMode.IntersectsWith);
```

### 数据库操作
```csharp
// 简化的数据库操作
using (var tr = db.TransactionManager.StartTransaction())
{
    var blockTable = tr.GetObject(db.BlockTableId, OpenMode.ForRead) as BlockTable;
    // 增强的操作...
    tr.Commit();
}
```

### 事务管理 (DBTrans)
```csharp
// 使用 DBTrans 进行事务操作
using var tr = new DBTrans();
var line = new Line(Point3d.Origin, new Point3d(100, 100, 0));
tr.CurrentSpace.AddEntity(line);
tr.Commit();
```

### 填充操作
```csharp
// 创建填充
var hatchInfo = new HatchInfo
{
    PatternName = "SOLID",
    PatternScale = 1.0,
    BoundaryIds = boundaryEntityIds
};

using var tr = new DBTrans();
var hatch = hatchInfo.CreateHatch();
tr.CurrentSpace.AddEntity(hatch);
tr.Commit();
```

### 符号表管理
```csharp
// 添加图层
using var tr = new DBTrans();
var layerTable = tr.LayerTable;
layerTable.Add("NewLayer", Color.FromColorIndex(ColorMethod.ByAci, 1));

// 添加文字样式
var textStyleTable = tr.TextStyleTable;
textStyleTable.Add("NewStyle", "arial.ttf", 2.5);
```

### 外部参照操作
```csharp
// 加载外部参照
using var tr = new DBTrans();
var xrefFactory = tr.XrefFactory(XrefModes.Attach, null);
xrefFactory.AttachXref("drawing.dwg", "XrefBlock", Point3d.Origin);
```

## 主要功能模块详解

### 1. 数据结构和算法

#### 四叉树 (QuadTree)

高效的空间数据结构，用于快速查询和碰撞检测。

**核心类：**
- `QuadTree<TEntity>` - 四叉树根节点控制器
- `QuadTreeNode<TEntity>` - 四叉树子节点
- `QuadEntity` - 四叉树图元
- `QuadTreeEvn` - 四叉树环境变量

#### QuadTree<T> 类详细方法

**构造函数：**
```csharp
public QuadTree(Rect rect)
```
- **参数：** `rect` - 四叉树的矩形范围
- **用途：** 创建四叉树根节点控制器

**Insert 方法：**
```csharp
public void Insert(T ent)
```
- **参数：** `ent` - 要插入的数据项
- **用途：** 通过根节点插入数据项到四叉树中

**Query 方法：**
```csharp
public List<T> Query(Rect rect, QuadTreeSelectMode selectMode)
```
- **参数：**
  - `rect` - 矩形选区查询范围
  - `selectMode` - 查询模式（IntersectsWith/Contains）
- **返回值：** 查询结果列表
- **用途：** 查询四叉树，返回给定区域的数据项

**Remove 方法重载：**
```csharp
// 根据范围删除
public void Remove(Rect rect)

// 根据图元删除
public void Remove(T ent)
```
- **参数：**
  - `rect` - 要删除的矩形范围
  - `ent` - 要删除的图元
- **用途：** 删除指定范围或图元的子节点

**FindNeibor 方法：**
```csharp
public List<T> FindNeibor(Rect rect, QuadTreeFindMode findMode)
```
- **参数：**
  - `rect` - 查找的矩形区域
  - `findMode` - 查找方向模式（Left/Right/Top/Bottom等）
- **返回值：** 附近节点图元列表
- **用途：** 找到指定方向的附近节点图元

**FindNearEntity 方法：**
```csharp
public List<T> FindNearEntity(Rect rect)
```
- **参数：** `rect` - 查找的矩形区域
- **返回值：** 附近图元列表
- **用途：** 找到附近的所有图元

**ForEach 方法：**
```csharp
public void ForEach(QTAction action)
```
- **参数：** `action` - 要执行的操作委托
- **用途：** 对四叉树中的每个节点执行特定操作

**使用示例：**

**基本四叉树操作：**
```csharp
// 创建四叉树
var boundary = new Rect(0, 0, 1000, 1000);
var quadTree = new QuadTree<Entity>(boundary);

// 插入实体
using (var tr = new DBTrans())
{
    var entities = tr.CurrentSpace.GetEntities<Entity>();
    foreach (var entity in entities)
    {
        quadTree.Insert(entity);
    }
}

// 查询指定区域的实体
var queryRect = new Rect(100, 100, 200, 200);
var foundEntities = quadTree.Query(queryRect, QuadTreeSelectMode.IntersectsWith);
Console.WriteLine($"找到 {foundEntities.Count} 个相交的实体");

// 查询完全包含在区域内的实体
var containedEntities = quadTree.Query(queryRect, QuadTreeSelectMode.Contains);
Console.WriteLine($"找到 {containedEntities.Count} 个完全包含的实体");
```

**邻近查找示例：**
```csharp
// 查找附近的实体
var searchRect = new Rect(500, 500, 50, 50);
var nearEntities = quadTree.FindNearEntity(searchRect);
Console.WriteLine($"附近找到 {nearEntities.Count} 个实体");

// 查找特定方向的邻居
var leftNeighbors = quadTree.FindNeibor(searchRect, QuadTreeFindMode.Left);
var rightNeighbors = quadTree.FindNeibor(searchRect, QuadTreeFindMode.Right);
var topNeighbors = quadTree.FindNeibor(searchRect, QuadTreeFindMode.Top);
var bottomNeighbors = quadTree.FindNeibor(searchRect, QuadTreeFindMode.Bottom);

Console.WriteLine($"左侧邻居: {leftNeighbors.Count}");
Console.WriteLine($"右侧邻居: {rightNeighbors.Count}");
Console.WriteLine($"上方邻居: {topNeighbors.Count}");
Console.WriteLine($"下方邻居: {bottomNeighbors.Count}");
```

**删除和遍历操作：**
```csharp
// 删除指定区域的所有实体
var deleteRect = new Rect(200, 200, 100, 100);
quadTree.Remove(deleteRect);

// 删除特定实体
var entityToRemove = foundEntities.FirstOrDefault();
if (entityToRemove != null)
{
    quadTree.Remove(entityToRemove);
}

// 遍历所有节点并执行操作
quadTree.ForEach((node, entities) =>
{
    Console.WriteLine($"节点包含 {entities.Count} 个实体");
    // 对每个实体执行操作
    foreach (var entity in entities)
    {
        Console.WriteLine($"  实体ID: {entity.ObjectId}");
    }
});
```

#### 矩形类 (Rect)

提供矩形操作的完整功能集。

**主要属性：**
- X, Y, Left, Right, Top, Bottom, Width, Height, Area
- MinPoint, MaxPoint, CenterPoint（几何点）

**主要功能：**
- 矩形创建和操作
- 包含关系检测
- 碰撞检测
- 点积和叉积计算
- 列扫碰撞检测算法

### 2. 数据库操作

#### 事务管理 (DBTrans)

简化的事务操作封装，提供更便捷的数据库访问方式和事务栈管理。

**核心类：**
- `DBTrans` - 事务栈管理
- `DatabaseEx` - 数据库扩展方法
- `SwitchDatabase` - 自动切换活动数据库

#### DBTrans 类详细方法

**静态方法：**

**GetTopTransaction 方法：**
```csharp
public static Transaction GetTopTransaction(Database database)
```
- **参数：** `database` - 目标数据库
- **返回值：** 顶层事务对象
- **用途：** 获取指定数据库的当前顶层事务

**GetTop 方法：**
```csharp
public static DBTrans GetTop(Database database)
```
- **参数：** `database` - 目标数据库
- **返回值：** 顶层DBTrans事务对象
- **异常：** 参数为null时抛出 `ArgumentNullEx`
- **用途：** 获取指定数据库的顶层DBTrans事务

**构造函数重载：**

**文档构造函数：**
```csharp
public DBTrans(Document doc, bool commit = true, bool docLock = false)
```
- **参数：**
  - `doc` - 要打开的文档
  - `commit` - 是否自动提交事务（默认true）
  - `docLock` - 是否锁定文档（默认false）
- **用途：** 基于文档创建事务，支持文档锁定

**数据库构造函数：**
```csharp
public DBTrans(Database database, bool commit = true)
```
- **参数：**
  - `database` - 要打开的数据库
  - `commit` - 是否自动提交事务（默认true）
- **用途：** 基于数据库创建事务

**文件构造函数：**
```csharp
public DBTrans(string fileName, bool commit = true, FileOpenMode fileOpenMode = FileOpenMode.OpenForReadAndAllShare, string password = "", bool docLock = false)
```
- **参数：**
  - `fileName` - 要打开的文件名
  - `commit` - 是否自动提交事务
  - `fileOpenMode` - 文件打开模式
  - `password` - 文件密码
  - `docLock` - 是否锁定文档
- **用途：** 直接从文件创建事务

**核心方法：**

**GetObject 方法：**
```csharp
public DBObject GetObject(ObjectId id, OpenMode openMode = OpenMode.ForRead, bool openErased = false, bool openLockedLayer = false)
```
- **参数：**
  - `id` - 对象ID
  - `openMode` - 打开模式（默认只读）
  - `openErased` - 是否打开已删除对象（默认false）
  - `openLockedLayer` - 是否打开锁定图层对象（默认false）
- **返回值：** 数据库对象

**GetObject<T> 泛型方法：**
```csharp
public T GetObject<T>(ObjectId id, OpenMode openMode = OpenMode.ForRead, bool openErased = false, bool openLockedLayer = false) where T : DBObject
```
- **类型参数：** `T` - 要获取的对象类型
- **返回值：** 指定类型的数据库对象

**Task 方法：**
```csharp
public void Task(Action action, bool isForeground = true)
```
- **参数：**
  - `action` - 要执行的操作
  - `isForeground` - 是否在前台执行（默认true）
- **用途：** 前台后台任务分别处理
- **备注：**
  - 文字偏移问题主要出现在线性引擎函数上
  - 后台处理利用前台当前数据库进行处理

**事务控制方法：**

**Commit 方法：**
```csharp
public void Commit()
```
- **功能：** 提交当前事务

**Abort 方法：**
```csharp
public void Abort()
```
- **功能：** 取消当前事务

**隐式转换：**
```csharp
public static implicit operator Transaction(DBTrans tr)
```
- **功能：** 将DBTrans隐式转换为Transaction对象

**使用示例：**
```csharp
// 静态方法使用
var topTransaction = DBTrans.GetTopTransaction(database);
var topDBTrans = DBTrans.GetTop(database);

// 不同构造方式
// 1. 基于当前文档
using (var tr = new DBTrans())
{
    var line = new Line(Point3d.Origin, new Point3d(100, 100, 0));
    tr.CurrentSpace.AddEntity(line);
    tr.Commit();
}

// 2. 基于特定数据库
using (var tr = new DBTrans(targetDatabase))
{
    var entity = tr.GetObject<Entity>(objectId, OpenMode.ForWrite);
    entity.Color = Color.FromColorIndex(ColorMethod.ByAci, 1);
    tr.Commit();
}

// 3. 基于文件
using (var tr = new DBTrans(@"C:\Drawing.dwg", true, FileOpenMode.OpenForReadAndAllShare))
{
    // 处理外部文件
    tr.Commit();
}

// 4. 前台后台任务处理
using (var tr = new DBTrans())
{
    tr.Task(() =>
    {
        // 在后台执行的操作
        var entities = tr.CurrentSpace.GetEntities<Line>();
        foreach (var line in entities)
        {
            line.Color = Color.FromColorIndex(ColorMethod.ByAci, 2);
        }
    }, false); // false表示后台执行

    tr.Commit();
}

// 5. 文档锁定模式
using (var tr = new DBTrans(document, true, true)) // 第三个参数为true表示锁定文档
{
    // 在锁定状态下执行操作
    tr.Commit();
}
```

#### 字典操作 (DBDictionaryEx)

扩展字典操作功能，支持各种数据类型的存储和检索。

**主要功能：**
- 扩展数据管理
- 编组操作
- 数据表创建
- 子字典管理

### 3. 图形实体扩展

#### 实体操作 (EntityEx)

为各种 AutoCAD 实体提供扩展方法，包括变换操作、属性设置和几何计算。

#### EntityEx 类详细方法

**移动操作：**

**Move 方法重载：**
```csharp
// 基于两点移动
public static void Move(Entity ent, Point3d from, Point3d to)

// 基于向量移动
public static void Move(Entity ent, Vector3d vector)
```
- **参数：**
  - `ent` - 要移动的实体
  - `from` - 移动起点
  - `to` - 移动终点
  - `vector` - 移动向量
- **用途：** 移动实体到新位置

**缩放操作：**

**Scale 方法：**
```csharp
public static void Scale(Entity ent, Point3d center, double scaleFactor)
```
- **参数：**
  - `ent` - 要缩放的实体
  - `center` - 缩放基点坐标
  - `scaleFactor` - 缩放比例
- **用途：** 按指定比例缩放实体

**旋转操作：**

**Rotation 方法重载：**
```csharp
// 3D旋转
public static void Rotation(Entity ent, Point3d center, double angle, Vector3d axis)

// XY平面旋转
public static void Rotation(Entity ent, Point3d center, double angle)
```
- **参数：**
  - `ent` - 要旋转的实体
  - `center` - 旋转中心
  - `angle` - 旋转角度（弧度）
  - `axis` - 旋转轴向量（3D旋转）
- **用途：** 旋转实体

**镜像操作：**

**Mirror 方法重载：**
```csharp
// 按对称轴镜像
public static void Mirror(Entity ent, Point3d startPoint, Point3d endPoint)

// 按对称面镜像
public static void Mirror(Entity ent, Plane plane)

// 按对称点镜像
public static void Mirror(Entity ent, Point3d basePoint)
```
- **参数：**
  - `ent` - 要镜像的实体
  - `startPoint` - 对称轴起点
  - `endPoint` - 对称轴终点
  - `plane` - 对称平面
  - `basePoint` - 对称点
- **用途：** 镜像实体

**几何信息获取：**

**GetExtents 方法：**
```csharp
public static Extents3d GetExtents(IEnumerable<Entity> ents)
```
- **参数：** `ents` - 实体迭代器
- **返回值：** 实体集合的范围
- **用途：** 获取多个实体的总体范围

**GetBoundingBoxEx 方法：**
```csharp
public static BoundingBox GetBoundingBoxEx(Entity ent)
```
- **参数：** `ent` - 实体
- **返回值：** 包围盒信息
- **用途：** 获取图元包围盒

**GetStretchPoints 方法：**
```csharp
public static Point3dCollection GetStretchPoints(Entity ent)
```
- **参数：** `ent` - 实体
- **返回值：** 拉伸点集合
- **用途：** 获取实体的拉伸点

**使用示例：**

**基本变换操作：**
```csharp
using (var tr = new DBTrans())
{
    var entity = tr.GetObject<Entity>(entityId, OpenMode.ForWrite);

    // 移动实体
    EntityEx.Move(entity, Point3d.Origin, new Point3d(100, 100, 0));

    // 旋转实体（绕原点旋转45度）
    EntityEx.Rotation(entity, Point3d.Origin, Math.PI / 4);

    // 缩放实体（放大2倍）
    EntityEx.Scale(entity, Point3d.Origin, 2.0);

    // 镜像实体（以Y轴为对称轴）
    EntityEx.Mirror(entity, Point3d.Origin, new Point3d(0, 100, 0));

    tr.Commit();
}
```

**批量操作示例：**
```csharp
using (var tr = new DBTrans())
{
    var entities = tr.CurrentSpace.GetEntities<Entity>();

    // 获取所有实体的总体范围
    var totalExtents = EntityEx.GetExtents(entities);
    Console.WriteLine($"总体范围: {totalExtents.MinPoint} 到 {totalExtents.MaxPoint}");

    // 批量移动所有实体
    var moveVector = new Vector3d(50, 50, 0);
    foreach (var entity in entities)
    {
        entity.UpgradeOpen();
        EntityEx.Move(entity, moveVector);
    }

    tr.Commit();
}
```

**支持的实体类型：**
- 圆弧 (ArcEx)
- 圆 (CircleEx)
- 曲线 (CurveEx)
- 多段线 (PolylineEx)
- 文字 (DBTextEx, MTextEx)
- 块参照 (BlockReferenceEx)
- 面域 (RegionEx)

#### 几何计算 (GeometryEx)

提供丰富的几何计算功能。

**主要功能：**
- 点与多边形关系判断
- 向量计算
- 平面操作
- 点操作和变换

### 4. 用户交互

#### 编辑器扩展 (EditorEx)

增强的用户交互功能，提供选择集操作、用户输入、坐标变换和视图控制等功能。

#### EditorEx 类详细方法

**选择集操作：**

**SelectAtPoint 方法：**
```csharp
public static PromptSelectionResult SelectAtPoint(Editor editor, Point3d point, SelectionFilter filter = null)
```
- **参数：**
  - `editor` - 命令行对象
  - `point` - 选择点
  - `filter` - 选择过滤器（可选）
- **返回值：** 选择结果
- **用途：** 选择穿过一个点的对象

**SelectByLineWeight 方法：**
```csharp
public static PromptSelectionResult SelectByLineWeight(Editor editor, LineWeight lineWeight)
```
- **参数：**
  - `editor` - 命令行对象
  - `lineWeight` - 线宽
- **返回值：** 选择结果
- **用途：** 根据线宽创建图层选择集

**SSGet 方法：**
```csharp
public static PromptSelectionResult SSGet(Editor editor, string mode, SelectionFilter filter = null, (string, string)? message = null, Dictionary<string, (string, Action)> keywords = null)
```
- **参数：**
  - `editor` - 命令行对象
  - `mode` - 选择模式
  - `filter` - 选择过滤器
  - `message` - 提示消息
  - `keywords` - 关键字和回调
- **返回值：** 选择结果
- **用途：** 高级选择集操作

**消息和对话框：**

**StreamMessage 方法重载：**
```csharp
// 格式化消息
public static void StreamMessage(string format, params object[] args)

// 简单消息
public static void StreamMessage(string message)
```
- **参数：**
  - `format` - 带格式项的字符串
  - `args` - 格式化对象数组
  - `message` - 消息内容
- **用途：** 带错误提示对话框的打印信息

**InfoMessageBox 方法重载：**
```csharp
// 带标题的消息框
public static void InfoMessageBox(string caption, string message)

// 格式化消息框
public static void InfoMessageBox(string caption, string format, params object[] args)

// 默认标题消息框
public static void InfoMessageBox(string message)

// 格式化默认标题消息框
public static void InfoMessageBox(string format, params object[] args)
```
- **参数：**
  - `caption` - 对话框标题
  - `message` - 消息内容
  - `format` - 格式化字符串
  - `args` - 格式化参数
- **用途：** 显示提示信息对话框

**WriteMessage 方法重载：**
```csharp
// 简单消息
public static void WriteMessage(string message)

// 格式化消息
public static void WriteMessage(string format, params object[] args)
```
- **参数：**
  - `message` - 消息内容
  - `format` - 格式化字符串
  - `args` - 格式化参数
- **用途：** 命令行打印字符串

**状态检查：**

**HasEditor 方法：**
```csharp
public static bool HasEditor()
```
- **返回值：** 是否有活动的编辑器对象
- **用途：** 判断是否有活动的编辑器

**Acceptable 方法：**
```csharp
public static bool Acceptable()
```
- **返回值：** 是否可以打印字符串
- **用途：** 判断是否可以打印字符串

**矢量绘制：**

**DrawVectors 方法重载：**
```csharp
// 带闭合选项
public static void DrawVectors(Editor editor, IEnumerable<Point2d> pnts, short color, bool isClosed)

// 不闭合
public static void DrawVectors(Editor editor, IEnumerable<Point2d> pnts, short color)
```
- **参数：**
  - `editor` - 编辑器对象
  - `pnts` - 点表
  - `color` - 颜色
  - `isClosed` - 是否闭合
- **用途：** 画矢量线

**DrawCircles 方法：**
```csharp
public static void DrawCircles(Editor editor, IEnumerable<Point2d> pnts, short color, double radius, int sides)
```
- **参数：**
  - `editor` - 编辑器对象
  - `pnts` - 点表
  - `color` - 颜色
  - `radius` - 半径
  - `sides` - 边数
- **用途：** 用矢量线画近似圆（正多边形）

**DrawLineVectors 方法：**
```csharp
public static void DrawLineVectors(Editor editor, IEnumerable<Point3d> points, int color, bool isClosed)
```
- **参数：**
  - `editor` - 用户交互对象
  - `points` - 点表
  - `color` - 颜色
  - `isClosed` - 是否闭合
- **用途：** 根据点表绘制矢量线段（每两点为一条线段）

**DrawEndToEndVectors 方法：**
```csharp
public static void DrawEndToEndVectors(Editor editor, IEnumerable<Point3d> points, int color, bool isClosed, bool isVisible)
```
- **参数：**
  - `editor` - 用户交互对象
  - `points` - 点表
  - `color` - 颜色
  - `isClosed` - 是否闭合
  - `isVisible` - 是否可见
- **用途：** 根据点表绘制首尾相连的矢量

**坐标变换：**

**GetMatrixFromUcsToWcs 方法：**
```csharp
public static Matrix3d GetMatrixFromUcsToWcs(Editor editor)
```
- **参数：** `editor` - 命令行对象
- **返回值：** UCS到WCS的变换矩阵
- **用途：** 获取用户坐标系到世界坐标系的变换矩阵

**GetMatrixFromWcsToUcs 方法：**
```csharp
public static Matrix3d GetMatrixFromWcsToUcs(Editor editor)
```
- **参数：** `editor` - 命令行对象
- **返回值：** WCS到UCS的变换矩阵
- **用途：** 获取世界坐标系到用户坐标系的变换矩阵

**GetMatrix 方法：**
```csharp
public static Matrix3d GetMatrix(Editor editor, CoordinateSystemCode from, CoordinateSystemCode to)
```
- **参数：**
  - `editor` - 命令行对象
  - `from` - 源坐标系
  - `to` - 目标坐标系
- **返回值：** 变换矩阵
- **用途：** 获取任意坐标系之间的变换矩阵

**视图控制：**

**ZoomWindow 方法重载：**
```csharp
// 基于范围缩放
public static void ZoomWindow(Editor ed, Extents3d ext, double factor = 1.0)

// 基于两点缩放
public static void ZoomWindow(Editor ed, Point3d lpt, Point3d rpt, double factor = 1.0)
```
- **参数：**
  - `ed` - 命令行对象
  - `ext` - 窗口范围
  - `lpt` - 第一点
  - `rpt` - 第二点
  - `factor` - 缩放因子
- **用途：** 缩放窗口到指定范围

**Zoom 方法：**
```csharp
public static void Zoom(Editor ed, Point3d cenPt, double height, double width)
```
- **参数：**
  - `ed` - 命令行对象
  - `cenPt` - 中心点
  - `height` - 高度
  - `width` - 宽度
- **用途：** 按范围缩放

**ZoomExtents 方法：**
```csharp
public static void ZoomExtents(Editor ed, double offsetDist = 0.0)
```
- **参数：**
  - `ed` - 命令行对象
  - `offsetDist` - 偏移距离
- **用途：** 动态缩放到全部范围

**ZoomObject 方法：**
```csharp
public static void ZoomObject(Editor ed, Entity ent, double factor = 1.0)
```
- **参数：**
  - `ed` - 命令行对象
  - `ent` - 实体对象
  - `factor` - 缩放因子
- **用途：** 根据实体对象的范围显示视图

**用户输入：**

**GetPoint 方法：**
```csharp
public static PromptPointResult GetPoint(Editor ed, string message, Point3d basePoint)
```
- **参数：**
  - `ed` - 命令行对象
  - `message` - 提示信息
  - `basePoint` - 基点
- **返回值：** 点选择结果
- **用途：** 获取用户输入的点

**GetDouble 方法：**
```csharp
public static PromptDoubleResult GetDouble(Editor ed, string message, double defaultValue)
```
- **参数：**
  - `ed` - 命令行对象
  - `message` - 提示信息
  - `defaultValue` - 默认值
- **返回值：** 双精度数选择结果
- **用途：** 获取用户输入的双精度数

**GetInteger 方法：**
```csharp
public static PromptIntegerResult GetInteger(Editor ed, string message, int defaultValue)
```
- **参数：**
  - `ed` - 命令行对象
  - `message` - 提示信息
  - `defaultValue` - 默认值
- **返回值：** 整数选择结果
- **用途：** 获取用户输入的整数

**GetString 方法：**
```csharp
public static PromptResult GetString(Editor ed, string message, string defaultValue)
```
- **参数：**
  - `ed` - 命令行对象
  - `message` - 提示信息
  - `defaultValue` - 默认值
- **返回值：** 字符串选择结果
- **用途：** 获取用户输入的字符串

**高级功能：**

**RunLisp 方法：**
```csharp
public static void RunLisp(Editor ed, string lispCode, RunLispFlag flag)
```
- **参数：**
  - `ed` - 编辑器对象
  - `lispCode` - Lisp语句
  - `flag` - 执行标志
- **用途：** 发送Lisp语句字符串到CAD执行

**PrepareForJig 方法重载：**
```csharp
// 数组版本
public static void PrepareForJig(Editor ed, Entity[] ents)

// 集合版本
public static void PrepareForJig(Editor ed, IEnumerable<Entity> ents)
```
- **参数：**
  - `ed` - 命令栏
  - `ents` - 实体（已存在数据库中）
- **用途：** Jig前的准备工作，使图元暗显

**GetCurrentMouthPoint 方法：**
```csharp
public static Point3d? GetCurrentMouthPoint(Editor ed)
```
- **参数：** `ed` - 命令栏
- **返回值：** 鼠标当前位置坐标（可能为null）
- **用途：** 获取CAD鼠标当前位置坐标

**使用示例：**

**选择和消息示例：**
```csharp
var ed = Application.DocumentManager.MdiActiveDocument.Editor;

// 选择对象
var result = EditorEx.SelectAtPoint(ed, new Point3d(100, 100, 0));
if (result.Status == PromptStatus.OK)
{
    EditorEx.WriteMessage($"选择了 {result.Value.Count} 个对象");
}

// 显示消息
EditorEx.InfoMessageBox("提示", "操作完成！");
EditorEx.StreamMessage("处理了 {0} 个对象", result.Value.Count);
```

**用户输入示例：**
```csharp
var ed = Application.DocumentManager.MdiActiveDocument.Editor;

// 获取点
var pointResult = EditorEx.GetPoint(ed, "请选择一个点: ", Point3d.Origin);
if (pointResult.Status == PromptStatus.OK)
{
    var point = pointResult.Value;

    // 获取半径
    var radiusResult = EditorEx.GetDouble(ed, "请输入半径: ", 10.0);
    if (radiusResult.Status == PromptStatus.OK)
    {
        var radius = radiusResult.Value;

        // 创建圆
        using (var tr = new DBTrans())
        {
            var circle = new Circle(point, Vector3d.ZAxis, radius);
            tr.CurrentSpace.AddEntity(circle);
            tr.Commit();
        }

        EditorEx.WriteMessage("圆创建完成！");
    }
}
```

**视图控制示例：**
```csharp
var ed = Application.DocumentManager.MdiActiveDocument.Editor;

// 缩放到全部
EditorEx.ZoomExtents(ed);

// 缩放到指定窗口
var ext = new Extents3d(new Point3d(0, 0, 0), new Point3d(100, 100, 0));
EditorEx.ZoomWindow(ed, ext, 1.1);

// 缩放到特定对象
using (var tr = new DBTrans())
{
    var entity = tr.GetObject<Entity>(objectId);
    EditorEx.ZoomObject(ed, entity, 1.2);
}
```

**矢量绘制示例：**
```csharp
var ed = Application.DocumentManager.MdiActiveDocument.Editor;

// 绘制矢量线
var points = new List<Point2d>
{
    new Point2d(0, 0),
    new Point2d(100, 0),
    new Point2d(100, 100),
    new Point2d(0, 100)
};

EditorEx.DrawVectors(ed, points, 1, true); // 红色闭合线

// 绘制圆形
var centerPoints = new List<Point2d> { new Point2d(50, 50) };
EditorEx.DrawCircles(ed, centerPoints, 2, 25.0, 16); // 黄色圆，16边形近似
```

#### 选择集扩展 (SelectionSetEx)

提供更强大的选择集操作功能。

### 5. 系统管理

#### 环境管理 (Env)

系统变量和环境设置的统一管理。

**主要功能：**
- 系统变量管理
- 捕捉模式控制
- 标注设置
- 文档和数据库访问

#### 自动加载 (AutoReg)

程序集自动注册和初始化功能。

**核心类：**
- `AutoRegAssem` - 注册中心
- `IFoxAutoGo` - 自动执行接口
- `IFoxInitializeAttribute` - 初始化特性

### 6. 过滤器系统

#### 选择集过滤器 (OpFilter)

强大的选择集过滤功能。

**过滤器类型：**
- `OpEqual` - 相等过滤器
- `OpAnd` - 逻辑与
- `OpOr` - 逻辑或
- `OpNot` - 逻辑非
- `OpXor` - 逻辑异或

**使用示例：**
```csharp
// 创建过滤器
var filter = OpFilter.Build(
    OpEqual.Create(DxfCode.Start, "LINE"),
    OpEqual.Create(DxfCode.LayerName, "0")
);

// 应用过滤器选择
var selection = Env.Editor.SelectAll(filter.ToSelectionFilter());
```

### 7. 数据封装

#### 数据列表类

- `TypedValueList` - 通用数据列表，用于集中管理扩展数据/扩展字典/resultBuffer
- `XDataList` - 扩展数据列表
- `XRecordDataList` - 扩展字典数据列表
- `LispList` - Lisp 数据封装

### 8. 填充系统

#### 填充扩展 (HatchEx)

强大的填充操作功能，提供边界管理、样式设置和关联性处理。

**核心类：**
- `HatchEx` - 填充扩展类
- `HatchInfo` - 图案填充信息
- `HatchConverter` - 填充边界转换器
- `HatchDialog` - 填充图案选择对话框

#### HatchEx 类详细方法

**ForEach 方法：**
```csharp
public static void ForEach(Hatch hatch, Action<HatchLoop> action)
```
- **参数：**
  - `hatch` - 填充对象
  - `action` - 对每个边界环执行的操作
- **用途：** 遍历填充的每条边界环并执行指定操作

**GetAssociatedBoundaryIds 方法：**
```csharp
public static List<ObjectIdCollection> GetAssociatedBoundaryIds(Hatch hatch)
```
- **参数：** `hatch` - 填充对象
- **返回值：** 边界对象ID集合列表（每个边界环的所有对象ID组成一个ObjectIdCollection）
- **异常：** 参数无效时抛出 `ArgumentException`
- **用途：** 提取已存在的关联边界

**CreateBoundarys 方法：**
```csharp
public static List<DBObjectCollection> CreateBoundarys(Hatch hatch)
```
- **参数：** `hatch` - 填充对象
- **返回值：** 边界环列表（每个边界环的所有对象组成一个DBObjectCollection）
- **用途：** 创建边界对象（仅创建于内存中，未加入数据库）

**ResetBoundarys 方法：**
```csharp
public static void ResetBoundarys(Hatch hatch, List<ObjectIdCollection> boundaryIds, bool? associative = null)
```
- **参数：**
  - `hatch` - 填充对象
  - `boundaryIds` - 边界对象ID集合列表
  - `associative` - 是否关联（可选）
- **用途：** 重新设置边界并计算填充
- **注意事项：**
  - 边界必须是封闭的环，可以是一条线围合或多条线首尾相连围合
  - 多个外边界时，建议顺序为：外边界→外边界→外边界→普通边界，或外边界→普通边界→外边界→普通边界

**边界处理专用方法：**

**HatchLoopIsPolyline 方法：**
```csharp
public static void HatchLoopIsPolyline(HatchLoop loop, DBObjectCollection objColl)
```
- **参数：**
  - `loop` - 填充边界环
  - `objColl` - 收集边界图元的集合
- **用途：** 处理多段线类型的边界

**TwoArcFormOneCircle 方法：**
```csharp
public static void TwoArcFormOneCircle(HatchLoop loop, DBObjectCollection objColl)
```
- **参数：**
  - `loop` - 填充边界环
  - `objColl` - 收集边界图元的集合
- **用途：** 处理两个圆弧组成圆形的特殊情况

**HatchLoopIsCurve2d 方法：**
```csharp
public static void HatchLoopIsCurve2d(HatchLoop loop, DBObjectCollection objColl)
```
- **参数：**
  - `loop` - 填充边界环
  - `objColl` - 收集边界图元的集合
- **用途：** 处理2D曲线类型的边界

**使用示例：**

**基本边界操作：**
```csharp
using (var tr = new DBTrans())
{
    // 获取填充对象
    var hatch = tr.GetObject<Hatch>(hatchId, OpenMode.ForWrite);

    // 获取现有边界
    var boundaryIds = HatchEx.GetAssociatedBoundaryIds(hatch);
    Console.WriteLine($"填充包含 {boundaryIds.Count} 个边界环");

    // 遍历每个边界环
    HatchEx.ForEach(hatch, loop =>
    {
        Console.WriteLine($"边界类型: {loop.LoopType}");
        Console.WriteLine($"边界包含 {loop.Curves.Count} 个曲线");
    });

    tr.Commit();
}
```

**创建和重设边界：**
```csharp
using (var tr = new DBTrans())
{
    // 创建新的填充
    var hatch = new Hatch();
    tr.CurrentSpace.AddEntity(hatch);

    // 设置填充样式
    hatch.SetHatchPattern(HatchPatternType.PreDefined, "ANSI31");
    hatch.PatternScale = 1.0;

    // 创建边界（圆形）
    var circle = new Circle(Point3d.Origin, Vector3d.ZAxis, 50);
    tr.CurrentSpace.AddEntity(circle);

    // 设置边界
    var boundaryIds = new List<ObjectIdCollection>
    {
        new ObjectIdCollection { circle.ObjectId }
    };

    HatchEx.ResetBoundarys(hatch, boundaryIds, true); // 关联边界

    tr.Commit();
}
```

### 9. 符号表管理

#### 符号表扩展 (SymbolTableEx)

提供符号表的高级操作功能。

**核心类：**
- `SymbolTable<TTable, TRecord>` - 符号表管理类
- `SymbolTableEx` - 符号表扩展方法
- `SymbolTableRecordEx` - 符号表记录扩展

**主要功能：**
- 图层管理
- 文字样式管理
- 线型管理
- 块定义管理

### 10. Jig 交互

#### Jig 扩展 (JigEx)

增强的用户交互绘图功能。

**核心类：**
- `JigEx` - Jig 扩展类
- `JigExTransient` - 瞬态容器
- `WorldDrawEvent` - 重绘事件

**主要功能：**
- 动态绘图
- 实时预览
- 用户交互
- 瞬态图形

### 11. 外部参照管理

#### 外部参照扩展 (XrefEx)

完整的外部参照管理功能。

**核心类：**
- `XrefEx` - 外部参照扩展
- `XrefFactory` - 参照工厂类
- `XrefPath` - 外部参照路径管理
- `IXrefBindModes` - 参照绑定模式接口

**主要功能：**
- 外部参照加载和卸载
- 路径管理
- 绑定操作
- 参照状态管理

### 12. 系统变量管理

#### 系统变量管理器 (SystemVariableManager)

统一的系统变量管理接口。

**主要功能：**
- 系统变量读取和设置
- 批量变量操作
- 变量状态保存和恢复
- 环境配置管理

### 13. PE 文件分析

#### PE 文件信息分析系统

用于分析Windows PE（Portable Executable）文件结构，提供对AutoCAD相关DLL和EXE文件的深度分析能力。

**核心类：**
- `PeInfo` - PE文件信息分析主类
- `AcadPeInfo` - AutoCAD专用PE信息获取
- `PeFunction` - PE函数查找工具
- `DosHeader` - DOS文件头结构
- `PEHeader` - PE文件头结构
- `OptionalHeader` - PE扩展头结构
- `ExportDirectory` - 函数导出表
- `ImportDirectory` - 函数导入表
- `ResourceDirectory` - 资源表

#### PeInfo 主类

**构造函数：**
```csharp
public PeInfo(string fullName)
```
- **参数：** `fullName` - PE文件的完整路径
- **异常：** 文件不存在或格式错误时抛出 `ArgumentException`

**主要属性：**
- `OpenFile` - 文件是否正常打开
- `ExportDirectory` - 函数接口名单
- `FullName` - PE文件完整路径

**主要方法：**

**LoadFile 方法：**
```csharp
public void LoadFile()
```
- **功能：** 开始读取和解析PE文件结构

**LoadDosHeader 方法：**
```csharp
public void LoadDosHeader()
```
- **功能：** 获取DOS文件头信息

**LoadPEHeader 方法：**
```csharp
public bool LoadPEHeader()
```
- **功能：** 获取PE文件头信息
- **返回值：** 是否成功加载

**LoadExportDirectory 方法：**
```csharp
public void LoadExportDirectory()
```
- **功能：** 读取函数导出表

**GetPETable 方法：**
```csharp
public DataSet GetPETable()
```
- **功能：** 获取完整的PE信息数据集
- **返回值：** 包含多个表的数据集

**使用示例：**
```csharp
// 分析AutoCAD核心DLL
var peInfo = new PeInfo(@"C:\Program Files\Autodesk\AutoCAD 2024\accore.dll");

try
{
    peInfo.LoadFile();

    if (peInfo.OpenFile)
    {
        Console.WriteLine($"成功加载PE文件: {peInfo.FullName}");

        // 获取导出函数列表
        var exportDir = peInfo.ExportDirectory;
        var functionNames = exportDir.FunctionNames();

        Console.WriteLine($"导出函数数量: {functionNames.Count}");
        foreach (var funcName in functionNames.Take(10)) // 显示前10个
        {
            Console.WriteLine($"  - {funcName}");
        }

        // 获取完整PE信息表
        var peDataSet = peInfo.GetPETable();
        Console.WriteLine($"PE信息表数量: {peDataSet.Tables.Count}");
    }
}
catch (ArgumentException ex)
{
    Console.WriteLine($"PE文件分析失败: {ex.Message}");
}
```

#### AcadPeInfo 类

专门用于获取AutoCAD相关PE文件的函数指针和接口信息。

**构造函数：**
```csharp
public AcadPeInfo(string methodName, AcadPeEnum acadPeEnum)
```
- **参数：**
  - `methodName` - 不带修饰的函数名
  - `acadPeEnum` - 读取的CAD文件类型枚举

**主要属性：**
- `PeForAcadExe` - AutoCAD主程序PE信息
- `PeForAccoreDll` - accore.dll PE信息
- `PeForAcdbDll` - acdb.dll PE信息
- `Methods` - 同名函数指针集合

**主要方法：**

**GetDelegate 方法：**
```csharp
public static TDelegate GetDelegate<TDelegate>(string methodName, AcadPeEnum acadPeEnum)
```
- **功能：** 获取CAD函数的委托指针
- **参数：**
  - `methodName` - 函数名
  - `acadPeEnum` - CAD文件类型
- **返回值：** 指定类型的委托

**使用示例：**
```csharp
// 获取AutoCAD内部函数指针
try
{
    // 定义函数委托类型
    [UnmanagedFunctionPointer(CallingConvention.Cdecl)]
    public delegate int AcedCommandDelegate(IntPtr cmdStr);

    // 获取acedCommand函数指针
    var acedCommand = AcadPeInfo.GetDelegate<AcedCommandDelegate>(
        "acedCommand",
        AcadPeEnum.AcadExe);

    if (acedCommand != null)
    {
        Console.WriteLine("成功获取acedCommand函数指针");
        // 可以调用AutoCAD内部函数
    }
}
catch (GetPeMethodException ex)
{
    Console.WriteLine($"获取函数指针失败: {ex.ErrorMsg}");
}
```

#### PeFunction 工具类

**主要方法：**

**Finds 方法：**
```csharp
public static void Finds(PeInfo peInfo, string findFuncName, List<PeFunction> funcAdress_Out)
```
- **功能：** 在PE文件中查找指定名称的所有函数
- **参数：**
  - `peInfo` - PE文件信息
  - `findFuncName` - 要查找的函数名
  - `funcAdress_Out` - 输出的函数集合

**高级应用示例：**
```csharp
// 批量分析AutoCAD相关DLL
public void AnalyzeAutoCadDlls()
{
    var cadPath = @"C:\Program Files\Autodesk\AutoCAD 2024\";
    var dllFiles = new[]
    {
        "accore.dll",
        "acdb24.dll",
        "acge24.dll",
        "acad.exe"
    };

    foreach (var fileName in dllFiles)
    {
        var fullPath = Path.Combine(cadPath, fileName);
        if (File.Exists(fullPath))
        {
            try
            {
                var peInfo = new PeInfo(fullPath);
                peInfo.LoadFile();

                if (peInfo.OpenFile)
                {
                    Console.WriteLine($"\n=== {fileName} ===");

                    // 查找特定函数
                    var functions = new List<PeFunction>();
                    PeFunction.Finds(peInfo, "acdb", functions);

                    Console.WriteLine($"找到 {functions.Count} 个acdb相关函数");

                    // 获取PE信息表
                    var dataSet = peInfo.GetPETable();
                    foreach (DataTable table in dataSet.Tables)
                    {
                        Console.WriteLine($"  表: {table.TableName}, 行数: {table.Rows.Count}");
                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine($"分析 {fileName} 失败: {ex.Message}");
            }
        }
    }
}
```

### 14. 窗口和UI扩展

#### 窗口扩展 (WindowEx)

窗体和用户界面扩展功能。

**核心类：**
- `WindowEx` - 窗体扩展
- `PaneEx` - 托盘类扩展
- `PaneMarginType` - 托盘边距类型

**主要功能：**
- 窗口操作
- 托盘管理
- UI布局控制
- 窗口事件处理

### 15. 文档锁管理

#### 文档锁管理器 (DocumentLockManager)

用于管理AutoCAD文档的安全锁定和解锁，确保多线程环境下的文档操作安全。

**核心类：**
- `DocumentLockManager` - 文档锁管理器
- `DocumentLockManagerExtension` - 文档锁管理扩展方法

**主要功能：**
- 自动文档锁定管理
- 安全的资源释放
- 多线程环境下的文档保护
- 简化的锁定操作接口

**使用场景：**
- 多线程AutoCAD应用程序
- 需要确保文档操作原子性的场景
- 防止文档并发访问冲突
- 自动化批处理操作

**基本用法：**
```csharp
// 使用扩展方法安全锁定文档
using (var lockManager = document.SecurelyLock())
{
    // 在锁定状态下执行文档操作
    using (var tr = document.Database.TransactionManager.StartTransaction())
    {
        // 安全的文档操作
        tr.Commit();
    }
} // 自动释放文档锁

// 手动创建文档锁管理器
var lockManager = new DocumentLockManager(document);
try
{
    // 执行需要锁定的操作
}
finally
{
    lockManager.Dispose(); // 手动释放
}
```

**高级用法：**
```csharp
// 检查锁定状态
using (var lockManager = document.SecurelyLock())
{
    if (!lockManager.IsDisposed)
    {
        // 执行操作
        Console.WriteLine("文档已安全锁定");
    }
}

// 在命令中使用文档锁
[CommandMethod("SAFE_OPERATION")]
public void SafeOperation()
{
    var doc = Application.DocumentManager.MdiActiveDocument;

    using (var lockManager = doc.SecurelyLock())
    {
        // 安全的文档操作
        using (var tr = new DBTrans())
        {
            // 执行数据库操作
            tr.Commit();
        }
    }
}
```

### 16. DWG文件标记

#### DWG文件标记管理 (DwgMark)

用于为DWG文件添加、移除和获取自定义标记，实现文件标识和版本管理功能。

**核心类：**
- `DwgMark` - DWG文件标记管理类

**主要功能：**
- 为DWG文件添加ASCII标识字节
- 移除文件标记，恢复默认值
- 获取文件的当前标记
- 文件完整性验证

**方法详解：**

**AddMark 方法：**
```csharp
public static void AddMark(FileInfo file, int bite)
```
- **参数：**
  - `file`: DWG文件信息
  - `bite`: ASCII标识字节 (0x00~0x7F)
- **异常：** 非DWG文件或字节超出范围时抛出 `ArgumentException`

**RemoveMark 方法：**
```csharp
public static void RemoveMark(FileInfo file)
```
- **参数：**
  - `file`: 要移除标记的DWG文件
- **异常：** 非DWG文件时抛出 `ArgumentException`

**GetMark 方法：**
```csharp
public static int GetMark(FileInfo file)
```
- **参数：**
  - `file`: 要获取标记的DWG文件
- **返回值：** 文件的当前标记字节
- **异常：** 非DWG文件时抛出 `ArgumentException`

**使用示例：**
```csharp
// 为DWG文件添加标记
var dwgFile = new FileInfo(@"C:\Drawings\sample.dwg");

try
{
    // 添加标记 (使用ASCII字符 'A' = 65)
    DwgMark.AddMark(dwgFile, 65);
    Console.WriteLine("标记添加成功");

    // 获取当前标记
    int currentMark = DwgMark.GetMark(dwgFile);
    Console.WriteLine($"当前标记: {currentMark} (字符: {(char)currentMark})");

    // 移除标记
    DwgMark.RemoveMark(dwgFile);
    Console.WriteLine("标记已移除");
}
catch (ArgumentException ex)
{
    Console.WriteLine($"操作失败: {ex.Message}");
}
```

**实际应用场景：**
```csharp
// 批量文件标记管理
public void BatchMarkFiles(string folderPath, int markValue)
{
    var dwgFiles = Directory.GetFiles(folderPath, "*.dwg")
                           .Select(f => new FileInfo(f));

    foreach (var file in dwgFiles)
    {
        try
        {
            DwgMark.AddMark(file, markValue);
            Console.WriteLine($"已标记文件: {file.Name}");
        }
        catch (ArgumentException)
        {
            Console.WriteLine($"跳过无效文件: {file.Name}");
        }
    }
}

// 版本标记系统
public enum DrawingVersion
{
    Draft = 68,      // 'D'
    Review = 82,     // 'R'
    Final = 70,      // 'F'
    Archive = 65     // 'A'
}

public void SetDrawingVersion(FileInfo dwgFile, DrawingVersion version)
{
    DwgMark.AddMark(dwgFile, (int)version);
}

public DrawingVersion GetDrawingVersion(FileInfo dwgFile)
{
    int mark = DwgMark.GetMark(dwgFile);
    return (DrawingVersion)mark;
}
```

### 17. 天正接口

#### 天正扩展 (TangentEx)

天正CAD接口支持。

**主要功能：**
- 天正比例获取
- 天正命令调用
- 天正数据交互

## 社区和支持

### 社区资源
- **QQ 群：** IFoxCad交流群
- **QQ 频道：** CAD二次开发
- **项目地址：** https://gitee.com/inspirefunction/ifoxcad
- **文档地址：** [IFoxCAD类库从入门到精通](https://www.kdocs.cn/l/cc6ZXSa0vMgD)
- **API 文档：** [IFoxCAD API 文档](https://inspirefunction.github.io/ifoxdoc/)

### 贡献指南

欢迎参与项目贡献：

1. 提交 Issue 报告问题或建议
2. 参与文档编写
3. Fork 项目并提交 Pull Request
4. 帮助完善功能和修复 Bug

## 性能优化

### 四叉树性能
- 对于空间查询，比线性搜索快得多
- 针对 CAD 实体碰撞检测进行了优化
- 可通过 QuadTreeEvn 配置深度和分割阈值

### 内存管理
- AutoCAD 对象的正确释放模式
- 自动事务管理工具
- 资源清理助手

### 碰撞检测优化

IFoxCAD 提供了比四叉树更快的列扫碰撞检测算法：

```csharp
Rect.XCollision(entities,
    firstProcessing: entity => false,
    collisionProcessing: (a, b) => { /* 处理碰撞 */ return false; },
    lastProcessing: entity => { /* 后处理 */ }
);
```

## 最佳实践

1. **处理大量实体时使用四叉树进行空间操作**
2. **利用扩展方法编写更清洁、可读的代码**
3. **使用事务助手进行适当的资源管理**
4. **对几何操作应用基于容差的比较**
5. **使用集合工具进行高效的数据操作**

该库通过提供高级抽象同时保持性能和灵活性，显著简化了 AutoCAD .NET 开发。

## 高级功能

### 1. 文档锁管理

```csharp
using var lockManager = document.SecurelyLock();
// 在锁定状态下执行操作
```

### 2. 系统变量管理

```csharp
// 临时修改系统变量
using var osmode = Env.SetOsmode(OSModeType.None);
// 操作完成后自动恢复
```

### 3. 自动初始化

```csharp
[IFoxInitialize]
public static void Initialize()
{
    // 程序集加载时自动执行
}

public class AutoRunner : IFoxAutoGo
{
    public int SequenceId() => 1;
    public void Go()
    {
        // 自动执行的代码
    }
}
```

## 详细 API 参考

### 四叉树系统类

#### QuadTree<T> 类
```csharp
public class QuadTree<T> where T : class
```

**主要成员：**
- `Count`: 四叉树中节点的数量
- `Insert(T entity)`: 将实体插入空间索引
- `Query(Rect rect, QuadTreeSelectMode selectMode)`: 查询矩形区域内的实体
- `Remove(Rect rect)`: 根据包围矩形删除实体
- `Remove(T entity)`: 删除特定实体
- `FindNeibor(Rect rect, QuadTreeFindMode findMode)`: 查找邻近实体
- `FindNearEntity(Rect rect)`: 查找矩形附近的实体
- `ForEach(QTAction action)`: 对所有节点执行操作

**选择模式：**
- `IntersectsWith`: 选择与查询矩形相交的实体
- `Contains`: 选择完全包含在查询矩形内的实体

**查找模式：**
- `Top`, `Bottom`, `Left`, `Right`: 方向性邻居搜索

#### QuadTreeNode<T> 类
```csharp
public class QuadTreeNode<T>
```

**象限属性：**
- `RightTopTree`: 第一象限（东北）
- `LeftTopTree`: 第二象限（西北）
- `LeftBottomTree`: 第三象限（西南）
- `RightBottomTree`: 第四象限（东南）

**主要属性：**
- `Nodes`: 所有子节点集合
- `NodesIsEmpty`: 所有子节点是否为空
- `Parent`: 父节点引用
- `Depth`: 节点在四叉树中的深度
- `Contents`: 此节点包含的实体
- `CountSubTree`: 子树中的实体总数

#### QuadTreeEvn 配置
```csharp
public static class QuadTreeEvn
```

**配置字段：**
- `MinArea`: 最小节点面积（必须 > 0）
- `SelectMode`: 默认选择模式
- `QuadTreeMaximumDepth`: 最大树深度
- `QuadTreeContentsCountSplit`: 节点分割的实体数量阈值

### 填充系统类

#### HatchEx 类
```csharp
public static class HatchEx
```

**主要方法：**
- `ForEach(Hatch hatch, Action<HatchLoop> action)`: 遍历填充循环
- `CreateHatch(HatchInfo hatchInfo)`: 创建填充对象
- `SetBoundary(Hatch hatch, ObjectIdCollection boundaryIds)`: 设置填充边界

#### HatchInfo 类
```csharp
public class HatchInfo
```

**主要属性：**
- `PatternName`: 图案名称
- `PatternScale`: 图案比例
- `PatternAngle`: 图案角度
- `BoundaryIds`: 边界实体ID集合
- `IsGradient`: 是否为渐变填充

**渐变填充：**
- `GradientName.Linear`: 线性渐变
- `GradientName.Cylindrical`: 圆柱渐变
- `GradientName.Inverted`: 反向渐变

### 符号表管理类

#### SymbolTable<TTable, TRecord> 类
```csharp
public class SymbolTable<TTable, TRecord>
```

**主要方法：**
- `Add(string name, ...)`: 添加符号表记录
- `Has(string name)`: 检查记录是否存在
- `GetRecord(string name)`: 获取记录
- `Remove(string name)`: 删除记录

#### SymbolTableEx 扩展
```csharp
public static class SymbolTableEx
```

**图层操作：**
- `Add(LayerTable table, string name, Color color)`: 添加图层
- `SetLayerColor(string layerName, Color color)`: 设置图层颜色
- `SetLayerLinetype(string layerName, string linetypeName)`: 设置图层线型

**文字样式操作：**
- `Add(TextStyleTable table, string name, string fontFile, double height)`: 添加文字样式

### 系统变量管理类

#### SystemVariableManager 类
```csharp
public class SystemVariableManager
```

**主要属性：**
- `ApBox`: 自动发布框
- `Attdia`: 属性对话框
- `Attreq`: 属性请求
- `Blipmode`: 标记模式
- `Cmdecho`: 命令回显

**使用示例：**
```csharp
var sysVarManager = new SystemVariableManager();
sysVarManager.Cmdecho = false; // 关闭命令回显
```

### Jig 交互类

#### JigEx 类
```csharp
public class JigEx : EntityJig
```

**事件：**
- `WorldDrawEvent`: 重绘事件

**主要方法：**
- `StartJig()`: 开始Jig操作
- `UpdateEntity()`: 更新实体
- `GetKeywords()`: 获取关键字

#### JigExTransient 类
```csharp
public class JigExTransient
```

**属性：**
- `Entities`: 瞬态实体集合

**方法：**
- `AddTransient(Entity entity)`: 添加瞬态实体
- `RemoveTransient(Entity entity)`: 移除瞬态实体
- `ClearTransients()`: 清除所有瞬态实体

### 几何类

#### Rect 类
```csharp
public struct Rect : IEquatable<Rect>, IFormattable, IComparable<Rect>
```

**核心属性：**
- `X`, `Y`: 位置坐标
- `Left`, `Bottom`, `Right`, `Top`: 边界坐标
- `Width`, `Height`: 尺寸
- `Area`: 计算面积
- `IsPoint`: 矩形是否表示单个点

**点属性：**
- `MinPoint`, `MaxPoint`: 角点（左下，右上）
- `CenterPoint`: 中心点
- `LeftLower`, `LeftMidst`, `LeftUpper`: 左边缘点
- `RightUpper`, `RightMidst`, `RightBottom`: 右边缘点
- `MidstUpper`, `MidstBottom`: 上/下中心点

**主要方法：**
- `Contains(Point2d point)`: 点包含测试
- `Contains(Rect rect)`: 矩形包含测试
- `IntersectsWith(Rect rect)`: 相交测试
- `Expand(double amount)`: 按量扩展矩形
- `ToPolyLine()`: 转换为 AutoCAD 多段线
- `ToPoints()`: 获取角点数组

**静态工具方法：**
- `GetMinMax(IEnumerable<Point2d> pts)`: 获取点的包围盒
- `IsRect(List<Point2d> pts, double tolerance)`: 测试点是否形成轴对齐矩形
- `IsRectAngle(List<Point2d> pts, double tolerance)`: 测试点是否形成旋转矩形
- `XCollision<T>()`: 高性能碰撞检测算法

#### BulgeVertexWidth 结构
```csharp
public struct BulgeVertexWidth
```

**属性：**
- `X`, `Y`: 顶点坐标
- `Bulge`: 弧凸度值
- `StartWidth`, `EndWidth`: 段宽度
- `Vertex`: Point2d 表示

**构造函数：**
- `BulgeVertexWidth(double x, double y, double bulge, double startWidth, double endWidth)`
- `BulgeVertexWidth(Point2d vertex, double bulge, double startWidth, double endWidth)`
- `BulgeVertexWidth(BulgeVertex bulgeVertex)`
- `BulgeVertexWidth(Polyline polyline, int index)`

### 扩展类

#### DatabaseEx 扩展
```csharp
public static class DatabaseEx
```

**主要方法：**
- `SwitchDatabase(Database db)`: 返回用于临时数据库切换的 IDisposable
- `SaveDwgFile(Database db, DwgVersion version)`: 使用特定版本保存
- `SaveFile(Database db, DwgVersion version, bool automatic, string saveAsFile, bool echoes)`: 高级保存选项

#### CollectionEx 扩展
```csharp
public static class CollectionEx
```

**集合转换方法：**
- `ToCollection(IEnumerable<ObjectId> ids)`: 转换为 ObjectIdCollection
- `ToCollection<T>(IEnumerable<T> objs)`: 转换为实体集合
- `ToCollection(IEnumerable<Point2d> pts)`: 转换为 Point2dCollection
- `ToCollection(IEnumerable<Point3d> pts)`: 转换为 Point3dCollection
- `ToList(ObjectIdCollection ids)`: 转换为 List<ObjectId>

**迭代方法：**
- `ForEach<T>(IEnumerable<T> source, Action<T> action)`: 简单迭代
- `ForEach<T>(IEnumerable<T> source, Action<int, T> action)`: 带索引的迭代
- `ForEach<T>(IEnumerable<T> source, Action<T, LoopState> action)`: 带中断控制的迭代

**关键字工具：**
- `Contains(KeywordCollection collection, string name, KeywordName keywordName)`: 检查关键字存在
- `ToDictionary(KeywordCollection collection)`: 转换为字典以实现 O(1) 查找

#### DBObjectEx 扩展
```csharp
public static class DBObjectEx
```

**对象管理：**
- `Erase(IEnumerable<DBObject> objects)`: 批量删除对象
- `CloneEx<T>(T obj)`: 增强的对象克隆
- `ForWrite<T>(T obj, Action<T> action)`: 自动写模式管理
- `ForWrite(DBObject obj)`: 返回写访问的升级管理器

**扩展数据方法：**
- `RemoveXData(DBObject obj, string appName)`: 删除应用程序的所有扩展数据
- `RemoveXData(DBObject obj, string appName, DxfCode dxfCode)`: 删除特定扩展数据
- `ChangeXData(DBObject obj, string appName, DxfCode dxfCode, object newValue)`: 修改扩展数据

### 外部参照管理类

#### XrefEx 扩展
```csharp
public static class XrefEx
```

**主要方法：**
- `XrefFactory(DBTrans tr, XrefModes mode, HashSet<string> xrefNames)`: 创建参照工厂

#### XrefFactory 类
```csharp
public class XrefFactory
```

**主要方法：**
- `AttachXref(string fileName, string blockName, Point3d insertPoint)`: 附加外部参照
- `DetachXref(string blockName)`: 分离外部参照
- `ReloadXref(string blockName)`: 重新加载外部参照
- `BindXref(string blockName)`: 绑定外部参照

**外部参照模式：**
- `XrefModes.Attach`: 附加模式
- `XrefModes.Overlay`: 覆盖模式
- `XrefModes.Bind`: 绑定模式
- `XrefModes.Detach`: 分离模式

### 实体扩展类

#### EntityEx 扩展
```csharp
public static class EntityEx
```

**变换操作：**
- `Move(Entity entity, Point3d from, Point3d to)`: 移动实体
- `Rotate(Entity entity, Point3d basePoint, double angle)`: 旋转实体
- `Scale(Entity entity, Point3d basePoint, double scaleFactor)`: 缩放实体
- `Mirror(Entity entity, Point3d point1, Point3d point2)`: 镜像实体

**属性操作：**
- `SetLayer(Entity entity, string layerName)`: 设置图层
- `SetColor(Entity entity, Color color)`: 设置颜色
- `SetLinetype(Entity entity, string linetypeName)`: 设置线型

#### 几何实体扩展

#### ArcEx - 圆弧扩展类

**CreateArcSCE 方法：**
```csharp
public static Arc CreateArcSCE(Point3d startPoint, Point3d centerPoint, Point3d endPoint)
```
- **参数：**
  - `startPoint` - 起点
  - `centerPoint` - 圆心
  - `endPoint` - 终点
- **返回值：** 创建的圆弧对象
- **用途：** 根据圆心、起点、终点创建圆弧（二维）

**CreateArc 方法重载：**
```csharp
// 三点法创建圆弧
public static Arc CreateArc(Point3d startPoint, Point3d pointOnArc, Point3d endPoint)

// 起点、圆心、角度法创建圆弧
public static Arc CreateArc(Point3d startPoint, Point3d centerPoint, double sweepAngle)
```
- **参数：**
  - `startPoint` - 起点
  - `pointOnArc` - 圆弧上的点
  - `endPoint` - 终点
  - `centerPoint` - 圆心
  - `sweepAngle` - 圆弧角度（弧度）
- **用途：** 不同方式创建圆弧

**ToPolyline 方法：**
```csharp
public static Polyline ToPolyline(Arc arc)
```
- **参数：** `arc` - 圆弧对象
- **返回值：** 转换后的多段线
- **用途：** 将圆弧转换为多段线

#### CircleEx - 圆扩展类

**CreateCircle 方法重载：**
```csharp
// 两点创建圆（两点中点为圆心）
public static Circle CreateCircle(Point3d startPoint, Point3d endPoint)

// 三点法创建圆
public static Circle CreateCircle(Point3d pt1, Point3d pt2, Point3d pt3)

// 圆心半径法创建圆
public static Circle CreateCircle(Point3d center, double radius, double startAngle, double endAngle, double thickness)
```
- **参数：**
  - `startPoint` - 起点
  - `endPoint` - 终点
  - `pt1`, `pt2`, `pt3` - 三个点
  - `center` - 圆心
  - `radius` - 半径
  - `startAngle` - 起始角度
  - `endAngle` - 结束角度
  - `thickness` - 厚度
- **返回值：** 创建的圆对象（三点法失败时返回null）
- **用途：** 不同方式创建圆

#### PolylineEx - 多段线扩展类

**GetPoints 方法重载：**
```csharp
// 获取二维多段线端点
public static List<Point3d> GetPoints(Polyline2d pl2d)

// 获取三维多段线端点
public static List<Point3d> GetPoints(Polyline3d pl3d)

// 获取多段线端点
public static List<Point3d> GetPoints(Polyline pl)
```
- **参数：** 不同类型的多段线对象
- **返回值：** 端点坐标集合
- **用途：** 获取多段线的所有端点坐标

**CreatePolyline 方法重载：**
```csharp
// 基于点集创建多段线
public static Polyline CreatePolyline(IEnumerable<Point3d> points, Action<Polyline> action = null)

// 基于复杂点集创建多段线
public static Polyline CreatePolyline(IEnumerable<(Point3d pt, double bulge, double startWidth, double endWidth)> pts, Action<Polyline> action = null)

// 基于Extents3d创建多段线
public static Polyline CreatePolyline(Extents3d extents, Action<Polyline> action = null)
```
- **参数：**
  - `points` - 点集
  - `pts` - 端点表（包含点、凸度、起始宽度、结束宽度）
  - `extents` - 三维范围
  - `action` - 多段线属性设置委托
- **返回值：** 创建的多段线对象
- **用途：** 不同方式创建多段线

**ToPolyline 方法重载：**
```csharp
// 2D点表生成多段线
public static Polyline ToPolyline(IEnumerable<Point2d> pointList, double plineWidth = 0, bool isClosed = false)

// 3D点表生成多段线
public static Polyline ToPolyline(IEnumerable<Point3d> pointList, double plineWidth = 0, bool isClosed = false)
```
- **参数：**
  - `pointList` - 点表
  - `plineWidth` - 线宽
  - `isClosed` - 是否闭合
- **返回值：** 生成的多段线
- **用途：** 从点表生成多段线

**使用示例：**

**圆弧操作示例：**
```csharp
using (var tr = new DBTrans())
{
    // 三点法创建圆弧
    var arc1 = ArcEx.CreateArc(
        new Point3d(0, 0, 0),
        new Point3d(50, 50, 0),
        new Point3d(100, 0, 0));
    tr.CurrentSpace.AddEntity(arc1);

    // 起点、圆心、终点法创建圆弧
    var arc2 = ArcEx.CreateArcSCE(
        new Point3d(0, 100, 0),
        new Point3d(50, 100, 0),
        new Point3d(100, 100, 0));
    tr.CurrentSpace.AddEntity(arc2);

    // 圆弧转多段线
    var polyline = ArcEx.ToPolyline(arc1);
    tr.CurrentSpace.AddEntity(polyline);

    tr.Commit();
}
```

**圆操作示例：**
```csharp
using (var tr = new DBTrans())
{
    // 两点创建圆
    var circle1 = CircleEx.CreateCircle(
        new Point3d(0, 0, 0),
        new Point3d(100, 100, 0));
    tr.CurrentSpace.AddEntity(circle1);

    // 三点法创建圆
    var circle2 = CircleEx.CreateCircle(
        new Point3d(200, 0, 0),
        new Point3d(250, 50, 0),
        new Point3d(300, 0, 0));

    if (circle2 != null) // 检查是否创建成功
    {
        tr.CurrentSpace.AddEntity(circle2);
    }

    tr.Commit();
}
```

**多段线操作示例：**
```csharp
using (var tr = new DBTrans())
{
    // 从点集创建多段线
    var points = new List<Point3d>
    {
        new Point3d(0, 0, 0),
        new Point3d(100, 0, 0),
        new Point3d(100, 100, 0),
        new Point3d(0, 100, 0)
    };

    var polyline = PolylineEx.CreatePolyline(points, pl =>
    {
        pl.Closed = true;
        pl.ConstantWidth = 5.0;
    });
    tr.CurrentSpace.AddEntity(polyline);

    // 获取多段线的所有点
    var extractedPoints = PolylineEx.GetPoints(polyline);
    Console.WriteLine($"多段线包含 {extractedPoints.Count} 个点");

    tr.Commit();
}
```

#### PInvokeUser32 系统API封装类

封装Windows User32.dll的常用API函数，提供窗口操作、消息处理和键盘输入等功能。

**窗口查找和管理：**

**FindWindow 方法：**
```csharp
public static IntPtr FindWindow(string lpClassName, string lpWindowName)
```
- **参数：**
  - `lpClassName` - 窗口类名
  - `lpWindowName` - 窗口标题
- **返回值：** 窗口句柄
- **用途：** 查找指定类名和标题的窗口

**GetForegroundWindow 方法：**
```csharp
public static IntPtr GetForegroundWindow()
```
- **返回值：** 当前前台窗口句柄
- **用途：** 获取当前活动窗口

**GetActiveWindow 方法：**
```csharp
public static IntPtr GetActiveWindow()
```
- **返回值：** 当前激活窗口句柄
- **用途：** 获取当前激活的窗口

**GetParent 方法：**
```csharp
public static IntPtr GetParent(IntPtr hWnd)
```
- **参数：** `hWnd` - 子窗口句柄
- **返回值：** 父窗口句柄
- **用途：** 获取指定窗口的父窗口

**GetWindow 方法：**
```csharp
public static IntPtr GetWindow(IntPtr hWnd, uint uCmd)
```
- **参数：**
  - `hWnd` - 窗口句柄
  - `uCmd` - 关系命令（GW_CHILD, GW_HWNDFIRST等）
- **返回值：** 相关窗口句柄
- **用途：** 检索指定窗口的相关窗口

**GetTopWindow 方法：**
```csharp
public static IntPtr GetTopWindow(IntPtr hWnd)
```
- **参数：** `hWnd` - 父窗口句柄
- **返回值：** 第一个子窗口句柄
- **用途：** 检索指定窗口的第一个子窗口

**窗口信息获取：**

**GetWindowText 方法：**
```csharp
public static int GetWindowText(IntPtr hWnd, StringBuilder lpString, int nMaxCount)
```
- **参数：**
  - `hWnd` - 窗口句柄
  - `lpString` - 接收文本的缓冲区
  - `nMaxCount` - 缓冲区大小
- **返回值：** 复制的字符数
- **用途：** 获取窗口标题

**GetWindowTextLength 方法：**
```csharp
public static int GetWindowTextLength(IntPtr hWnd)
```
- **参数：** `hWnd` - 窗口句柄
- **返回值：** 窗口标题长度
- **用途：** 获取窗口标题的字符长度

**GetClassName 方法：**
```csharp
public static int GetClassName(IntPtr hWnd, StringBuilder lpClassName, int nMaxCount)
```
- **参数：**
  - `hWnd` - 窗口句柄
  - `lpClassName` - 接收类名的缓冲区
  - `nMaxCount` - 缓冲区大小
- **返回值：** 复制的字符数
- **用途：** 获取窗口类名

**GetClientRect 方法：**
```csharp
public static bool GetClientRect(IntPtr hWnd, out WindowsAPI.IntRect lpRect)
```
- **参数：**
  - `hWnd` - 窗口句柄
  - `lpRect` - 输出的客户区矩形
- **返回值：** 是否成功
- **用途：** 获取窗口客户区大小

**消息处理：**

**SendMessage 方法重载：**
```csharp
// 基本版本
public static IntPtr SendMessage(IntPtr hWnd, uint Msg, IntPtr wParam, IntPtr lParam)

// 整数版本
public static IntPtr SendMessage(IntPtr hWnd, int Msg, IntPtr wParam, IntPtr lParam)
```
- **参数：**
  - `hWnd` - 目标窗口句柄
  - `Msg` - 消息类型
  - `wParam` - 消息参数1
  - `lParam` - 消息参数2
- **返回值：** 消息处理结果
- **用途：** 发送消息到指定窗口

**PostMessage 方法：**
```csharp
public static bool PostMessage(IntPtr hWnd, int Msg, IntPtr wParam, IntPtr lParam)
```
- **参数：**
  - `hWnd` - 目标窗口句柄
  - `Msg` - 消息类型
  - `wParam` - 消息参数1
  - `lParam` - 消息参数2
- **返回值：** 是否成功
- **用途：** 将消息放入目标线程的消息队列

**焦点和状态：**

**SetFocus 方法：**
```csharp
public static IntPtr SetFocus(IntPtr hWnd)
```
- **参数：** `hWnd` - 窗口句柄
- **返回值：** 之前拥有焦点的窗口句柄
- **用途：** 设置窗口焦点

**GetFocus 方法：**
```csharp
public static IntPtr GetFocus()
```
- **返回值：** 当前拥有焦点的窗口句柄
- **用途：** 获取当前焦点窗口

**IsWindowEnabled 方法：**
```csharp
public static bool IsWindowEnabled(IntPtr hWnd)
```
- **参数：** `hWnd` - 窗口句柄
- **返回值：** 窗口是否启用
- **用途：** 检查窗口是否启用

**IsIconic 方法：**
```csharp
public static bool IsIconic(int hWnd)
```
- **参数：** `hWnd` - 窗口句柄
- **返回值：** 窗口是否最小化
- **用途：** 检查窗口是否最小化

**键盘和输入：**

**KeybdEvent 方法：**
```csharp
public static void KeybdEvent(byte bVk, byte bScan, int dwFlags, int dwExtraInfo)
```
- **参数：**
  - `bVk` - 虚拟键码
  - `bScan` - 扫描码
  - `dwFlags` - 操作标志
  - `dwExtraInfo` - 额外信息
- **用途：** 模拟键盘按键

**GetKeyState 方法：**
```csharp
public static short GetKeyState(int nVirtKey)
```
- **参数：** `nVirtKey` - 虚拟键码
- **返回值：** 按键状态
- **用途：** 获取按键的当前状态

**GetKeyboardLayout 方法：**
```csharp
public static IntPtr GetKeyboardLayout(int idThread)
```
- **参数：** `idThread` - 线程ID
- **返回值：** 键盘布局句柄
- **用途：** 获取指定线程的输入法布局

**ToAscii 方法：**
```csharp
public static int ToAscii(int uVirtKey, int uScanCode, byte[] lpKeyState, byte[] lpChar, int uFlags)
```
- **参数：**
  - `uVirtKey` - 虚拟键码
  - `uScanCode` - 扫描码
  - `lpKeyState` - 键盘状态数组
  - `lpChar` - 输出字符缓冲区
  - `uFlags` - 标志
- **返回值：** 转换的字符数
- **用途：** 将虚拟键码转换为ASCII字符

**线程和进程：**

**GetWindowThreadProcessId 方法重载：**
```csharp
// 输出进程ID版本
public static uint GetWindowThreadProcessId(IntPtr hWnd, out uint lpdwProcessId)

// 输出进程ID版本（int）
public static uint GetWindowThreadProcessId(IntPtr hWnd, out int lpdwProcessId)
```
- **参数：**
  - `hWnd` - 窗口句柄
  - `lpdwProcessId` - 输出的进程ID
- **返回值：** 线程ID
- **用途：** 获取窗口对应的线程和进程ID

**GetGUIThreadInfo 方法：**
```csharp
public static bool GetGUIThreadInfo(uint idThread, ref GuiThreadInfo lpgui)
```
- **参数：**
  - `idThread` - 线程ID
  - `lpgui` - GUI线程信息结构
- **返回值：** 是否成功
- **用途：** 获取线程对应的窗体信息

#### WindowsAPI 系统工具类

提供更高级的Windows API封装，包括内存管理、数据转换和输入法控制等功能。

**内存管理：**

**GlobalLock 方法：**
```csharp
public static IntPtr GlobalLock(IntPtr hMem)
```
- **参数：** `hMem` - 内存句柄
- **返回值：** 内存指针
- **用途：** 锁定全局内存

**GlobalUnlock 方法：**
```csharp
public static bool GlobalUnlock(IntPtr hMem)
```
- **参数：** `hMem` - 内存句柄
- **返回值：** 是否成功
- **用途：** 解锁全局内存

**GlobalSize 方法：**
```csharp
public static uint GlobalSize(IntPtr hMem)
```
- **参数：** `hMem` - 内存句柄
- **返回值：** 内存块大小
- **用途：** 获取全局内存块大小

**GlobalLockTask 方法：**
```csharp
public static void GlobalLockTask(IntPtr hMem, Action<IntPtr> action)
```
- **参数：**
  - `hMem` - 内存句柄
  - `action` - 在锁定状态下执行的操作
- **用途：** 安全地锁定和释放内存

**数据转换：**

**BytesToStruct 方法重载：**
```csharp
// 带偏移版本
public static T BytesToStruct<T>(byte[] bytes, ref int offset) where T : struct

// 基本版本
public static T BytesToStruct<T>(byte[] bytes) where T : struct
```
- **类型参数：** `T` - 结构体类型
- **参数：**
  - `bytes` - 字节数组
  - `offset` - 偏移量（引用参数）
- **返回值：** 转换后的结构体
- **用途：** 将字节数组转换为结构体

**StructToBytes 方法：**
```csharp
public static byte[] StructToBytes<T>(T structObj) where T : unmanaged
```
- **类型参数：** `T` - 非托管结构体类型
- **参数：** `structObj` - 结构体对象
- **返回值：** 字节数组
- **用途：** 将结构体转换为字节数组

**DLL函数：**

**GetProcAddress 方法：**
```csharp
public static IntPtr GetProcAddress(IntPtr hModule, string procName)
```
- **参数：**
  - `hModule` - DLL模块句柄
  - `procName` - 函数名
- **返回值：** 函数地址
- **用途：** 获取DLL中函数的地址

**输入法控制：**

**ImmGetContext 方法：**
```csharp
public static IntPtr ImmGetContext(IntPtr hWnd)
```
- **参数：** `hWnd` - 窗口句柄
- **返回值：** 输入法上下文句柄
- **用途：** 获取指定窗口的输入法状态

**ImmSetOpenStatus 方法：**
```csharp
public static bool ImmSetOpenStatus(IntPtr hIMC, bool fOpen)
```
- **参数：**
  - `hIMC` - 输入法上下文句柄
  - `fOpen` - 是否打开输入法
- **返回值：** 是否成功
- **用途：** 设置输入法的开关状态

**ImmGetOpenStatus 方法：**
```csharp
public static bool ImmGetOpenStatus(IntPtr hIMC)
```
- **参数：** `hIMC` - 输入法上下文句柄
- **返回值：** 输入法是否打开
- **用途：** 获取输入法的开关状态

**ImmGetConversionStatus 方法：**
```csharp
public static bool ImmGetConversionStatus(IntPtr hIMC, out int lpfdwConversion, out int lpfdwSentence)
```
- **参数：**
  - `hIMC` - 输入法上下文句柄
  - `lpfdwConversion` - 输出转换模式
  - `lpfdwSentence` - 输出句子模式
- **返回值：** 是否成功
- **用途：** 获取输入法的转换状态

**ImmGetVirtualKey 方法：**
```csharp
public static uint ImmGetVirtualKey(IntPtr hWnd)
```
- **参数：** `hWnd` - 窗口句柄
- **返回值：** 虚拟键码
- **用途：** 获取输入法的虚拟键码

**系统工具：**

**CheckLowLevelHooksTimeout 方法：**
```csharp
public static void CheckLowLevelHooksTimeout(int timeoutMs)
```
- **参数：** `timeoutMs` - 超时时间（毫秒）
- **用途：** 设置低级钩子超时处理，防止系统限制

**CloseWindow 方法：**
```csharp
public static bool CloseWindow(IntPtr hWnd)
```
- **参数：** `hWnd` - 窗口句柄
- **返回值：** 是否成功
- **用途：** 关闭指定窗口

**使用示例：**

**窗口操作示例：**
```csharp
// 查找AutoCAD窗口
var acadWindow = PInvokeUser32.FindWindow("Afx:400000:b:10011:6:10", null);
if (acadWindow != IntPtr.Zero)
{
    // 获取窗口标题
    var titleLength = PInvokeUser32.GetWindowTextLength(acadWindow);
    var title = new StringBuilder(titleLength + 1);
    PInvokeUser32.GetWindowText(acadWindow, title, title.Capacity);

    Console.WriteLine($"找到AutoCAD窗口: {title}");

    // 设置焦点
    PInvokeUser32.SetFocus(acadWindow);

    // 获取客户区大小
    if (PInvokeUser32.GetClientRect(acadWindow, out var clientRect))
    {
        Console.WriteLine($"客户区大小: {clientRect.Width} x {clientRect.Height}");
    }
}
```

**消息发送示例：**
```csharp
// 发送键盘消息
var targetWindow = PInvokeUser32.GetForegroundWindow();
if (targetWindow != IntPtr.Zero)
{
    // 发送ESC键
    const int WM_KEYDOWN = 0x0100;
    const int VK_ESCAPE = 0x1B;

    PInvokeUser32.SendMessage(targetWindow, WM_KEYDOWN, new IntPtr(VK_ESCAPE), IntPtr.Zero);

    // 或者使用PostMessage异步发送
    PInvokeUser32.PostMessage(targetWindow, WM_KEYDOWN, new IntPtr(VK_ESCAPE), IntPtr.Zero);
}
```

**输入法控制示例：**
```csharp
var currentWindow = PInvokeUser32.GetForegroundWindow();
var imeContext = WindowsAPI.ImmGetContext(currentWindow);

if (imeContext != IntPtr.Zero)
{
    // 检查输入法状态
    bool isOpen = WindowsAPI.ImmGetOpenStatus(imeContext);
    Console.WriteLine($"输入法状态: {(isOpen ? "开启" : "关闭")}");

    // 关闭输入法
    if (isOpen)
    {
        WindowsAPI.ImmSetOpenStatus(imeContext, false);
        Console.WriteLine("输入法已关闭");
    }

    // 获取转换状态
    if (WindowsAPI.ImmGetConversionStatus(imeContext, out int conversion, out int sentence))
    {
        Console.WriteLine($"转换模式: {conversion}, 句子模式: {sentence}");
    }
}
```

**内存操作示例：**
```csharp
// 结构体与字节数组转换
public struct Point3D
{
    public double X, Y, Z;
}

var point = new Point3D { X = 1.0, Y = 2.0, Z = 3.0 };

// 结构体转字节数组
var bytes = WindowsAPI.StructToBytes(point);
Console.WriteLine($"结构体大小: {bytes.Length} 字节");

// 字节数组转结构体
var restoredPoint = WindowsAPI.BytesToStruct<Point3D>(bytes);
Console.WriteLine($"恢复的点: ({restoredPoint.X}, {restoredPoint.Y}, {restoredPoint.Z})");

// 安全的内存操作
IntPtr memHandle = /* 获取内存句柄 */;
WindowsAPI.GlobalLockTask(memHandle, ptr =>
{
    // 在锁定状态下操作内存
    // 自动解锁
});
```

**实际应用示例：**
```csharp
// CAD窗口管理工具
public class CadWindowManager
{
    public static void BringCadToFront()
    {
        var acadWindow = PInvokeUser32.FindWindow("Afx:400000:b:10011:6:10", null);
        if (acadWindow != IntPtr.Zero)
        {
            PInvokeUser32.SetFocus(acadWindow);

            // 如果窗口最小化，先恢复
            if (PInvokeUser32.IsIconic((int)acadWindow))
            {
                const int SW_RESTORE = 9;
                PInvokeUser32.SendMessage(acadWindow, 0x0112, new IntPtr(SW_RESTORE), IntPtr.Zero);
            }
        }
    }

    public static void DisableImeForCad()
    {
        var acadWindow = PInvokeUser32.FindWindow("Afx:400000:b:10011:6:10", null);
        if (acadWindow != IntPtr.Zero)
        {
            var imeContext = WindowsAPI.ImmGetContext(acadWindow);
            if (imeContext != IntPtr.Zero)
            {
                WindowsAPI.ImmSetOpenStatus(imeContext, false);
            }
        }
    }

    public static void SendEscapeToCAD()
    {
        var acadWindow = PInvokeUser32.FindWindow("Afx:400000:b:10011:6:10", null);
        if (acadWindow != IntPtr.Zero)
        {
            const int WM_KEYDOWN = 0x0100;
            const int VK_ESCAPE = 0x1B;
            PInvokeUser32.PostMessage(acadWindow, WM_KEYDOWN, new IntPtr(VK_ESCAPE), IntPtr.Zero);
        }
    }
}
```

#### RandomEx 随机数扩展类

提供增强的随机数生成功能，支持各种数据类型和范围的随机值生成。

**主要方法：**
- `NextDouble(double min, double max)` - 生成指定范围的随机双精度数
- `NextPoint3d(Point3d min, Point3d max)` - 生成随机三维点
- `NextColor()` - 生成随机颜色
- `NextBool(double probability)` - 按概率生成随机布尔值
- `NextString(int length, string chars)` - 生成随机字符串

**使用示例：**
```csharp
var random = new Random();

// 生成随机点
var randomPoint = RandomEx.NextPoint3d(
    new Point3d(0, 0, 0),
    new Point3d(100, 100, 0));

// 生成随机颜色
var randomColor = RandomEx.NextColor();

// 按70%概率生成true
var randomBool = RandomEx.NextBool(0.7);
```

#### SystemEx 系统扩展类

提供系统级操作的扩展方法，包括进程管理、文件操作和环境变量处理。

**主要方法：**
- `GetCurrentProcessName()` - 获取当前进程名称
- `IsProcessRunning(string processName)` - 检查进程是否运行
- `GetEnvironmentVariable(string name, string defaultValue)` - 安全获取环境变量
- `ExecuteCommand(string command, string arguments)` - 执行系统命令
- `GetSystemInfo()` - 获取系统信息

**使用示例：**
```csharp
// 检查AutoCAD是否运行
bool isAcadRunning = SystemEx.IsProcessRunning("acad");

// 获取环境变量
string cadPath = SystemEx.GetEnvironmentVariable("ACAD_PATH", @"C:\Program Files\Autodesk\AutoCAD 2024");

// 执行系统命令
var result = SystemEx.ExecuteCommand("dir", @"C:\");
```

#### DebugEx 调试工具类

提供增强的调试功能，包括性能测量、内存监控和日志记录。

**主要方法：**
- `Stopwatch(Action action, string description)` - 测量代码执行时间
- `MemoryUsage()` - 获取当前内存使用情况
- `WriteDebugInfo(string message, params object[] args)` - 写入调试信息
- `Assert(bool condition, string message)` - 断言检查
- `DumpObject(object obj)` - 输出对象详细信息

**使用示例：**
```csharp
// 性能测量
DebugEx.Stopwatch(() =>
{
    // 要测量的代码
    using (var tr = new DBTrans())
    {
        var entities = tr.CurrentSpace.GetEntities<Entity>();
        tr.Commit();
    }
}, "获取所有实体");

// 内存监控
var memInfo = DebugEx.MemoryUsage();
Console.WriteLine($"内存使用: {memInfo.WorkingSet / 1024 / 1024} MB");

// 调试断言
DebugEx.Assert(entities.Count() > 0, "实体数量应该大于0");
```

#### EnumEx 枚举扩展类

提供枚举类型的扩展操作，包括描述获取、值转换和验证功能。

**主要方法：**
- `GetDescription<T>(T enumValue)` - 获取枚举的描述特性
- `GetValues<T>()` - 获取枚举的所有值
- `Parse<T>(string value, bool ignoreCase)` - 安全解析枚举
- `IsDefined<T>(object value)` - 检查值是否为有效枚举
- `GetNames<T>()` - 获取枚举的所有名称

**使用示例：**
```csharp
// 获取枚举描述
var description = EnumEx.GetDescription(OpenMode.ForRead);

// 安全解析枚举
if (EnumEx.TryParse<OpenMode>("ForWrite", out var mode))
{
    Console.WriteLine($"解析成功: {mode}");
}

// 获取所有枚举值
var allModes = EnumEx.GetValues<OpenMode>();
foreach (var openMode in allModes)
{
    Console.WriteLine($"模式: {openMode}");
}
```

#### ArgumentNullEx 参数验证类

提供参数空值检查和验证功能，增强代码的健壮性。

**主要方法：**
- `ThrowIfNull(object argument, string paramName)` - 空值检查
- `ThrowIfNullOrEmpty(string argument, string paramName)` - 字符串空值检查
- `ThrowIfNullOrWhiteSpace(string argument, string paramName)` - 字符串空白检查
- `ThrowIfOutOfRange<T>(T value, T min, T max, string paramName)` - 范围检查
- `ThrowIfNegative(int value, string paramName)` - 负数检查

**使用示例：**
```csharp
public void ProcessEntity(Entity entity, string layerName, double scale)
{
    // 参数验证
    ArgumentNullEx.ThrowIfNull(entity, nameof(entity));
    ArgumentNullEx.ThrowIfNullOrWhiteSpace(layerName, nameof(layerName));
    ArgumentNullEx.ThrowIfOutOfRange(scale, 0.1, 10.0, nameof(scale));

    // 安全执行操作
    entity.Layer = layerName;
    // ... 其他操作
}
```

### 编辑器扩展类

#### EditorEx 扩展
```csharp
public static class EditorEx
```

**选择操作：**
- `SelectAtPoint(Editor editor, Point3d point)`: 点选实体
- `SelectByFilter(Editor editor, SelectionFilter filter)`: 按过滤器选择
- `SelectCrossingWindow(Editor editor, Point3d pt1, Point3d pt2)`: 交叉窗口选择
- `SelectWindow(Editor editor, Point3d pt1, Point3d pt2)`: 窗口选择

**用户输入：**
- `GetPoint(Editor editor, string message)`: 获取点
- `GetDistance(Editor editor, string message)`: 获取距离
- `GetAngle(Editor editor, string message)`: 获取角度
- `GetKeyword(Editor editor, string message, params string[] keywords)`: 获取关键字

**Lisp 执行：**
- `RunLisp(Editor editor, string lispCode)`: 执行Lisp代码
- `RunLisp(Editor editor, string lispCode, RunLispFlag flag)`: 带标志执行Lisp

### 窗口和UI扩展

#### WindowEx 扩展
```csharp
public static class WindowEx
```

**窗口操作：**
- `AddEscQuit(Window window)`: 添加ESC退出功能
- `SetWindowScale(Window window, double scale)`: 设置窗口比例
- `CenterWindow(Window window)`: 居中窗口

#### PaneEx 扩展
```csharp
public static class PaneEx
```

**托盘操作：**
- `SetMargin(Pane pane, PaneMarginType horizontal, PaneMarginType vertical)`: 设置边距
- `SetDockEnabled(Pane pane, bool enabled)`: 设置停靠启用

**边距类型：**
- `PaneMarginType.NONE`: 无边距
- `PaneMarginType.LEFT`: 左边距
- `PaneMarginType.RIGHT`: 右边距
- `PaneMarginType.TOP`: 上边距
- `PaneMarginType.BOTTOM`: 下边距

#### DBDictionaryEx 扩展
```csharp
public static class DBDictionaryEx
```

**字典操作：**
- `GetAllObjects<T>(DBDictionary dict)`: 获取特定类型的所有对象
- `GetData<T>(DBDictionary dict, string key)`: 按键获取类型化对象
- `SetData<T>(DBDictionary dict, string key, T newValue)`: 添加/更新字典条目

**XRecord 操作：**
- `GetXRecord(DBDictionary dict, string key)`: 获取扩展记录
- `SetXRecord(DBDictionary dict, string key, XRecordDataList rb)`: 设置扩展记录

**编组管理：**
- `AddGroup(DBDictionary dict, string name, ObjectIdCollection ids)`: 创建实体组
- `GetGroups(DBDictionary dict, Func<Group, bool> func)`: 使用过滤器查询组
- `GetGroups(Entity ent)`: 获取包含实体的组
- `RemoveNullGroup(DBDictionary dict)`: 删除空组

**工具方法：**
- `GetXDictionary(DBObject obj, OpenMode openMode)`: 获取扩展字典
- `GetSubDictionary(DBDictionary dict, bool createSubDictionary, IEnumerable<string> dictNames)`: 导航嵌套字典

### 容差和比较类

#### TolerancePoint2d 类
```csharp
public class TolerancePoint2d : IEqualityComparer<Point2d>
```

**用途：** 为 LINQ Distinct 操作提供基于容差的点比较

**构造函数：**
- `TolerancePoint2d(double tolerance)`: 使用容差值初始化

**方法：**
- `Equals(Point2d a, Point2d b)`: 在容差范围内比较点
- `GetHashCode(Point2d obj)`: 为点生成哈希码

### IFoxCAD.Basal 命名空间详细API

#### ArrayEx 数组扩展类

高性能数组操作扩展，提供数组合并、去重等功能。

**Combine2 方法：**
```csharp
public static T[] Combine2<T>(T[] a, T[] b)
```
- **类型参数：** `T` - 数组元素类型
- **参数：**
  - `a` - 第一个数组
  - `b` - 第二个数组
- **返回值：** 合并后的新数组
- **用途：** 高效合并两个数组

**Deduplication 方法：**
```csharp
public static List<T> Deduplication<T>(List<T> list, Func<T, T, bool> equalityComparer)
```
- **类型参数：** `T` - 列表元素类型
- **参数：**
  - `list` - 要去重的列表
  - `equalityComparer` - 相等性比较函数
- **返回值：** 去重后的列表
- **用途：** 按自定义规则对列表进行去重
- **说明：** 适用于数值类型比较和特定规则比较，对于哈希比较建议使用HashSet

**使用示例：**
```csharp
// 数组合并
var array1 = new int[] { 1, 2, 3 };
var array2 = new int[] { 4, 5, 6 };
var combined = ArrayEx.Combine2(array1, array2);
// 结果: [1, 2, 3, 4, 5, 6]

// 自定义去重
var points = new List<Point3d>
{
    new Point3d(0, 0, 0),
    new Point3d(0.001, 0.001, 0),
    new Point3d(1, 1, 0)
};

var deduped = ArrayEx.Deduplication(points, (p1, p2) =>
    p1.DistanceTo(p2) < 0.01); // 距离小于0.01认为是重复点
// 结果: 去除了距离过近的重复点
```

#### LinqEx LINQ扩展类

增强的LINQ操作，提供高级查找、排序和比较功能。

**FindByMax 方法重载：**
```csharp
// 基本版本
public static TValue FindByMax<TValue, TKey>(IEnumerable<TValue> source, Func<TValue, TKey> keySelector)

// 带输出键值版本
public static TValue FindByMax<TValue, TKey>(IEnumerable<TValue> source, out TKey maxKey, Func<TValue, TKey> keySelector)

// 比较器版本
public static TValue FindByMax<TValue>(IEnumerable<TValue> source, Comparison<TValue> comparison)
```
- **类型参数：**
  - `TValue` - 值类型
  - `TKey` - 键类型
- **参数：**
  - `source` - 源序列
  - `keySelector` - 键选择函数
  - `maxKey` - 输出的最大键值
  - `comparison` - 比较器
- **返回值：** 具有最大键值的元素
- **用途：** 按转换函数或比较器找出序列中最大键值的对应值

**FindByMin 方法重载：**
```csharp
// 基本版本
public static TValue FindByMin<TValue, TKey>(IEnumerable<TValue> source, Func<TValue, TKey> keySelector)

// 带输出键值版本
public static TValue FindByMin<TValue, TKey>(IEnumerable<TValue> source, out TKey minKey, Func<TValue, TKey> keySelector)

// 比较器版本
public static TValue FindByMin<TValue>(IEnumerable<TValue> source, Comparison<TValue> comparison)
```
- **类型参数：**
  - `TValue` - 值类型
  - `TKey` - 键类型
- **参数：**
  - `source` - 源序列
  - `keySelector` - 键选择函数
  - `minKey` - 输出的最小键值
  - `comparison` - 比较器
- **返回值：** 具有最小键值的元素
- **用途：** 按转换函数或比较器找出序列中最小键值的对应值

**FindByExt 方法重载：**
```csharp
// 转换函数版本
public static (TValue min, TValue max) FindByExt<TValue, TKey>(IEnumerable<TValue> source, Func<TValue, TKey> keySelector)

// 比较器版本
public static (TValue min, TValue max) FindByExt<TValue>(IEnumerable<TValue> source, Comparison<TValue> comparison)
```
- **参数：**
  - `source` - 源序列
  - `keySelector` - 键选择函数
  - `comparison` - 比较器
- **返回值：** 包含最小值和最大值的元组
- **用途：** 一次性找出序列中的最小值和最大值

**FindExt 方法：**
```csharp
public static (TKey min, TKey max) FindExt<TValue, TKey>(IEnumerable<TValue> source, Func<TValue, TKey> keySelector)
```
- **参数：**
  - `source` - 源序列
  - `keySelector` - 键选择函数
- **返回值：** 包含最小键值和最大键值的元组
- **用途：** 按转换函数找出序列中最小和最大键值

**OrderBy 方法：**
```csharp
public static IOrderedEnumerable<T> OrderBy<T, TKey>(IEnumerable<T> source, Func<T, TKey> keySelector, Comparison<TKey> comparison)
```
- **类型参数：**
  - `T` - 输入类型
  - `TKey` - 键类型
- **参数：**
  - `source` - 源序列
  - `keySelector` - 键选择函数
  - `comparison` - 比较器
- **返回值：** 排序后的序列
- **用途：** 使用指定的比较器将序列按升序排序

**ThenBy 方法：**
```csharp
public static IOrderedEnumerable<T> ThenBy<T, TKey>(IOrderedEnumerable<T> source, Func<T, TKey> keySelector, Comparison<TKey> comparison)
```
- **类型参数：**
  - `T` - 输入类型
  - `TKey` - 键类型
- **参数：**
  - `source` - 已排序的序列
  - `keySelector` - 键选择函数
  - `comparison` - 比较器
- **返回值：** 进一步排序后的序列
- **用途：** 使用指定的比较器将其后的序列按升序排序

**使用示例：**

**查找最值示例：**
```csharp
var entities = new List<Entity> { /* 实体列表 */ };

// 找出面积最大的实体
var largestEntity = entities.FindByMax(e => e.GeometricExtents.Area());

// 找出距离原点最近的实体
var nearestEntity = entities.FindByMin(e => e.GeometricExtents.MinPoint.DistanceTo(Point3d.Origin));

// 同时找出最大和最小面积的实体
var (minAreaEntity, maxAreaEntity) = entities.FindByExt(e => e.GeometricExtents.Area());

// 找出面积的最小值和最大值
var (minArea, maxArea) = entities.FindExt(e => e.GeometricExtents.Area());

Console.WriteLine($"面积范围: {minArea} - {maxArea}");
```

**自定义排序示例：**
```csharp
var points = new List<Point3d>
{
    new Point3d(1, 2, 0),
    new Point3d(3, 1, 0),
    new Point3d(2, 3, 0)
};

// 按距离原点的距离排序
var sortedByDistance = points.OrderBy(
    p => p.DistanceTo(Point3d.Origin),
    (d1, d2) => d1.CompareTo(d2));

// 先按X坐标排序，再按Y坐标排序
var sortedByXY = points
    .OrderBy(p => p.X, (x1, x2) => x1.CompareTo(x2))
    .ThenBy(p => p.Y, (y1, y2) => y1.CompareTo(y2));

foreach (var point in sortedByXY)
{
    Console.WriteLine($"点: ({point.X}, {point.Y})");
}
```

**实际应用示例：**
```csharp
// CAD实体处理示例
using (var tr = new DBTrans())
{
    var allEntities = tr.CurrentSpace.GetEntities<Entity>();

    // 找出最大的实体
    var largestEntity = allEntities.FindByMax(e =>
    {
        var ext = e.GeometricExtents;
        return (ext.MaxPoint.X - ext.MinPoint.X) * (ext.MaxPoint.Y - ext.MinPoint.Y);
    });

    // 按图层名称排序实体
    var entitiesByLayer = allEntities.OrderBy(
        e => e.Layer,
        (layer1, layer2) => string.Compare(layer1, layer2, StringComparison.OrdinalIgnoreCase));

    // 去除重复的圆（按中心点和半径）
    var circles = tr.CurrentSpace.GetEntities<Circle>();
    var uniqueCircles = ArrayEx.Deduplication(circles.ToList(), (c1, c2) =>
        c1.Center.IsEqualTo(c2.Center, new Tolerance(0.001, 0.001)) &&
        Math.Abs(c1.Radius - c2.Radius) < 0.001);

    Console.WriteLine($"去重前: {circles.Count()}, 去重后: {uniqueCircles.Count}");

    tr.Commit();
}
```

#### LoopList 环链表类

高性能的环形双向链表实现，支持循环遍历和高效的节点操作。

**核心类：**
- `LoopList<T>` - 环链表主类
- `LoopListNode<T>` - 环链表节点类

#### LoopList<T> 主要方法

**构造函数：**
```csharp
// 默认构造函数
public LoopList()

// 从集合构造
public LoopList(IEnumerable<T> values)
```
- **参数：** `values` - 节点迭代器
- **用途：** 创建环链表

**节点管理：**

**SetFirst 方法：**
```csharp
public LoopListNode<T> SetFirst(LoopListNode<T> node)
```
- **参数：** `node` - 要设置为首节点的节点
- **返回值：** 设置的首节点
- **用途：** 设置首节点

**Swap 方法：**
```csharp
public void Swap(LoopListNode<T> node1, LoopListNode<T> node2)
```
- **参数：**
  - `node1` - 第一个节点
  - `node2` - 第二个节点
- **用途：** 交换两个节点的值

**Reverse 方法：**
```csharp
public void Reverse()
```
- **用途：** 链内翻转，反转整个环链表的顺序

**添加操作：**

**AddFirst 方法：**
```csharp
public LoopListNode<T> AddFirst(T value)
```
- **参数：** `value` - 节点值
- **返回值：** 新创建的节点
- **用途：** 在首节点之前插入节点，并设置新节点为首节点

**Add / AddLast 方法：**
```csharp
public LoopListNode<T> Add(T value)
public LoopListNode<T> AddLast(T value)
```
- **参数：** `value` - 节点值
- **返回值：** 新创建的节点
- **用途：** 在尾节点之后插入节点，并设置新节点为尾节点

**AddRange 方法：**
```csharp
public void AddRange(IEnumerable<T> list)
```
- **参数：** `list` - 要添加的值集合
- **用途：** 将容器内容全部加入到末尾

**AddBefore 方法：**
```csharp
public LoopListNode<T> AddBefore(LoopListNode<T> node, T value)
```
- **参数：**
  - `node` - 参考节点
  - `value` - 新节点值
- **返回值：** 新创建的节点
- **用途：** 在指定节点前面增加节点

**AddAfter 方法：**
```csharp
public LoopListNode<T> AddAfter(LoopListNode<T> node, T value)
```
- **参数：**
  - `node` - 参考节点
  - `value` - 新节点值
- **返回值：** 新创建的节点
- **用途：** 在指定节点后面增加节点

**删除操作：**

**RemoveFirst 方法：**
```csharp
public bool RemoveFirst()
```
- **返回值：** 是否成功删除
- **用途：** 删除首节点

**RemoveLast 方法：**
```csharp
public bool RemoveLast()
```
- **返回值：** 是否成功删除
- **用途：** 删除尾节点

**Remove 方法重载：**
```csharp
// 删除指定节点
public bool Remove(LoopListNode<T> node)

// 删除所有包含指定值的节点
public bool Remove(T value)
```
- **参数：**
  - `node` - 要删除的节点
  - `value` - 要删除的值
- **返回值：** 是否成功删除
- **用途：** 删除节点或值

**查找操作：**

**Contains 方法重载：**
```csharp
// 检查是否包含节点
public bool Contains(LoopListNode<T> node)

// 检查是否包含值
public bool Contains(T value)
```
- **参数：**
  - `node` - 要查找的节点
  - `value` - 要查找的值
- **返回值：** 是否包含
- **用途：** 检查环链表是否包含指定节点或值

**Find 方法：**
```csharp
public LoopListNode<T> Find(T value)
```
- **参数：** `value` - 要查找的值
- **返回值：** 第一个匹配的节点，未找到返回null
- **用途：** 查找第一个出现的节点

**Finds 方法：**
```csharp
public List<LoopListNode<T>> Finds(T value)
```
- **参数：** `value` - 要查找的值
- **返回值：** 所有匹配的节点列表
- **用途：** 查找所有出现的节点

**GetNode 方法：**
```csharp
public LoopListNode<T> GetNode(Func<T, bool> func)
```
- **参数：** `func` - 查找条件函数
- **返回值：** 第一个匹配条件的节点
- **用途：** 按条件获取节点

**遍历操作：**

**ForEach 方法：**
```csharp
public void ForEach(Func<LoopListNode<T>, bool> action)
```
- **参数：** `action` - 对每个节点执行的操作，返回false停止遍历
- **用途：** 从头遍历所有节点

**For 方法：**
```csharp
public void For(Func<int, LoopListNode<T>, bool> action)
```
- **参数：** `action` - 对每个节点执行的操作，包含索引参数
- **用途：** 从头遍历所有节点（带计数）

**高级操作：**

**LinkTo 方法重载：**
```csharp
// 基本链接
public void LinkTo(LoopListNode<T> from, LoopListNode<T> to)

// 带计数的链接
public void LinkTo(LoopListNode<T> from, LoopListNode<T> to, int count)

// 完整参数的链接
public void LinkTo(LoopListNode<T> from, LoopListNode<T> to, int count, bool forward)
```
- **参数：**
  - `from` - 起始节点
  - `to` - 目标节点
  - `count` - 计数
  - `forward` - 方向
- **用途：** 链接两节点，并去除这两个节点间的所有节点

**GetNodes 方法重载：**
```csharp
// 从指定节点开始获取节点查询器
public IEnumerable<LoopListNode<T>> GetNodes(LoopListNode<T> from)

// 从首节点开始获取节点查询器
public IEnumerable<LoopListNode<T>> GetNodes()
```
- **参数：** `from` - 起始节点
- **返回值：** 节点查询器
- **用途：** 获取节点的查询器

#### LoopListNode<T> 节点类方法

**构造函数：**
```csharp
public LoopListNode(T value, LoopList<T> ts)
```
- **参数：**
  - `value` - 节点值
  - `ts` - 所属环链表
- **用途：** 创建环链表节点

**GetNext 方法：**
```csharp
public LoopListNode<T> GetNext(bool forward)
```
- **参数：** `forward` - 搜索方向标志，true为向前搜索，false为向后搜索
- **返回值：** 临近节点
- **用途：** 获取当前节点的临近节点

**Invalidate 方法：**
```csharp
public void Invalidate()
```
- **用途：** 无效化节点成员

**使用示例：**

**基本操作示例：**
```csharp
// 创建环链表
var loopList = new LoopList<int>();

// 添加元素
var node1 = loopList.Add(1);
var node2 = loopList.Add(2);
var node3 = loopList.Add(3);

Console.WriteLine($"环链表大小: {loopList.Count}");

// 在指定位置插入
var newNode = loopList.AddAfter(node2, 25);

// 遍历环链表
loopList.ForEach(node =>
{
    Console.WriteLine($"节点值: {node.Value}");
    return true; // 继续遍历
});
```

**查找和删除示例：**
```csharp
var loopList = new LoopList<string>(new[] { "A", "B", "C", "B", "D" });

// 查找第一个"B"
var firstB = loopList.Find("B");
Console.WriteLine($"找到第一个B的位置: {firstB?.Value}");

// 查找所有"B"
var allBs = loopList.Finds("B");
Console.WriteLine($"找到 {allBs.Count} 个B");

// 按条件查找
var longString = loopList.GetNode(s => s.Length > 1);

// 删除所有"B"
loopList.Remove("B");
Console.WriteLine($"删除后大小: {loopList.Count}");
```

**高级操作示例：**
```csharp
var loopList = new LoopList<Point3d>();

// 添加点
var points = new[]
{
    new Point3d(0, 0, 0),
    new Point3d(10, 0, 0),
    new Point3d(10, 10, 0),
    new Point3d(0, 10, 0)
};
loopList.AddRange(points);

// 反转环链表
loopList.Reverse();

// 交换两个节点的值
var first = loopList.First;
var last = loopList.Last;
loopList.Swap(first, last);

// 获取节点并遍历
foreach (var node in loopList.GetNodes())
{
    var next = node.GetNext(true); // 获取下一个节点
    var prev = node.GetNext(false); // 获取上一个节点

    Console.WriteLine($"当前: {node.Value}");
    Console.WriteLine($"下一个: {next.Value}");
    Console.WriteLine($"上一个: {prev.Value}");
}
```

**实际应用示例：**
```csharp
// CAD中的多段线顶点处理
public void ProcessPolylineVertices(Polyline polyline)
{
    var vertices = new LoopList<Point2d>();

    // 添加所有顶点
    for (int i = 0; i < polyline.NumberOfVertices; i++)
    {
        vertices.Add(polyline.GetPoint2dAt(i));
    }

    // 如果是闭合多段线，可以循环处理
    if (polyline.Closed)
    {
        vertices.ForEach(node =>
        {
            var current = node.Value;
            var next = node.GetNext(true).Value;

            // 计算边长
            var length = current.GetDistanceTo(next);
            Console.WriteLine($"边长: {length}");

            return true; // 继续遍历
        });
    }

    // 简化顶点（移除共线点）
    vertices.ForEach(node =>
    {
        var prev = node.GetNext(false).Value;
        var current = node.Value;
        var next = node.GetNext(true).Value;

        // 检查是否共线
        var vec1 = current - prev;
        var vec2 = next - current;

        if (Math.Abs(vec1.GetAngleTo(vec2)) < 0.01) // 角度小于0.01弧度
        {
            vertices.Remove(node);
        }

        return true;
    });

    Console.WriteLine($"简化后顶点数: {vertices.Count}");
}
```

#### LinqEx LINQ扩展
```csharp
public static class LinqEx
```

**查找方法：**
- `FindByMax<T, TKey>(IEnumerable<T> source, Func<T, TKey> selector)`: 查找最大值对应的元素
- `FindByMin<T, TKey>(IEnumerable<T> source, Func<T, TKey> selector)`: 查找最小值对应的元素
- `MaxBy<T, TKey>(IEnumerable<T> source, Func<T, TKey> selector)`: 获取最大键值
- `MinBy<T, TKey>(IEnumerable<T> source, Func<T, TKey> selector)`: 获取最小键值

**自定义比较器：**
- `SpecComparer<T>`: 自定义的比较泛型类

#### LoopList<T> 环链表
```csharp
public class LoopList<T> : IEnumerable<T>
```

**主要属性：**
- `Count`: 节点数量
- `Current`: 当前节点
- `IsEmpty`: 是否为空

**主要方法：**
- `Add(T item)`: 添加节点
- `Remove(T item)`: 删除节点
- `MoveNext()`: 移动到下一个节点
- `MovePrevious()`: 移动到上一个节点
- `Clear()`: 清空链表

#### SystemEx 系统扩展
```csharp
public static class SystemEx
```

**进程操作：**
- `CloseProc(string processName)`: 关闭指定进程

#### RandomEx 随机扩展
```csharp
public static class RandomEx
```

**随机方法：**
- `NextDouble(Random random, double min, double max)`: 生成指定范围的随机双精度数
- `NextBool(Random random)`: 生成随机布尔值
- `NextColor(Random random)`: 生成随机颜色

#### WindowsAPI 系统API
```csharp
public static class WindowsAPI
```

**API方法：**
- `GetProcAddress(IntPtr hModule, string procName)`: 获取过程地址
- `LoadLibrary(string lpFileName)`: 加载库
- `FreeLibrary(IntPtr hModule)`: 释放库
- `GetModuleHandle(string lpModuleName)`: 获取模块句柄

**键盘钩子：**
- `KeyboardHookStruct`: Hook键盘数据结构
- `CheckLowLevelHooksTimeout(int timeout)`: 检查低级钩子超时

#### PInvokeUser32 User32封装
```csharp
public static class PInvokeUser32
```

**窗口操作：**
- `FindWindow(string lpClassName, string lpWindowName)`: 查找窗口
- `SetWindowPos(IntPtr hWnd, IntPtr hWndInsertAfter, int x, int y, int cx, int cy, uint uFlags)`: 设置窗口位置
- `ShowWindow(IntPtr hWnd, int nCmdShow)`: 显示窗口
- `GetWindowText(IntPtr hWnd, StringBuilder lpString, int nMaxCount)`: 获取窗口文本

**线程信息：**
- `GuiThreadInfo`: 获取线程对应的窗体信息结构

#### DebugEx 调试工具
```csharp
public static class DebugEx
```

**调试方法：**
- `Printl(object obj, bool time = false)`: 打印调试信息

#### EnumEx 枚举扩展
```csharp
public static class EnumEx
```

**枚举操作：**
- `CleanCache()`: 清理枚举缓存
- `GetValues<T>()`: 获取枚举值
- `GetNames<T>()`: 获取枚举名称

#### ArgumentNullEx 参数检查
```csharp
public static class ArgumentNullEx
```

**参数验证：**
- `ThrowIfNull(object argument, string parameterName)`: 参数为空时抛出异常
- `ThrowIfNullOrEmpty(string argument, string parameterName)`: 字符串为空或null时抛出异常

## 实用示例

### 扩展数据管理
```csharp
// 添加扩展数据到实体
var xdataList = new XRecordDataList
{
    { DxfCode.ExtendedDataApplicationName, "MyApp" },
    { DxfCode.ExtendedDataAsciiString, "CustomData" },
    { DxfCode.ExtendedDataReal, 123.45 }
};

entity.XData = xdataList.ToResultBuffer();

// 检索和修改扩展数据
var appName = "MyApp";
entity.ChangeXData(appName, DxfCode.ExtendedDataReal, 678.90);

// 删除扩展数据
entity.RemoveXData(appName);
```

### 编组管理
```csharp
// 创建和管理实体组
var groupDict = tr.GetObject(db.GroupDictionaryId, OpenMode.ForWrite) as DBDictionary;
var entityIds = selectedEntities.GetObjectIds().ToCollection();

// 创建组
var groupId = groupDict.AddGroup("MyGroup", entityIds);

// 查找包含特定实体的组
var groups = entity.GetGroups();

// 删除空组
var removedGroups = groupDict.RemoveNullGroup();
```

### 安全属性修改
```csharp
// 安全修改实体属性
entity.ForWrite(ent =>
{
    ent.Color = Color.FromColorIndex(ColorMethod.ByAci, 1); // 红色
    ent.Layer = "NewLayer";
});

// 或使用升级管理器
using (var upgrader = entity.ForWrite())
{
    entity.Color = Color.FromColorIndex(ColorMethod.ByAci, 2); // 黄色
    entity.Linetype = "DASHED";
}
```

## 错误处理

### CAD 错误信息处理 (ErrorInfoEx)

专门用于处理和显示AutoCAD相关错误信息的工具类。

**核心类：**
- `ErrorInfoEx` - CAD错误信息处理类
- `GetPeMethodException` - PE方法专用异常类

#### ErrorInfoEx 类

**主要方法：**

**AcErrorInfo 方法：**
```csharp
public static void AcErrorInfo(AcException acex)
```
- **参数：** `acex` - AutoCAD异常对象
- **功能：** 将CAD错误信息格式化输出到命令行
- **用途：** 统一的错误信息显示和调试

**使用示例：**
```csharp
try
{
    // AutoCAD 操作代码
    using (var tr = new DBTrans())
    {
        // 可能抛出异常的操作
        var entity = tr.GetObject<Entity>(objectId);
        tr.Commit();
    }
}
catch (AcException acex)
{
    // 使用IFoxCAD的错误处理
    ErrorInfoEx.AcErrorInfo(acex);
}
catch (Exception ex)
{
    // 处理其他类型异常
    Console.WriteLine($"一般错误: {ex.Message}");
}
```

#### GetPeMethodException 类

专门用于PE（Protocol Extension）方法调用时的异常处理。

**主要属性：**
- `ErrorNum` - 错误编号
- `ErrorMsg` - 错误消息
- `InnerException1` - 内部异常

**构造函数：**
```csharp
// 基本构造函数
public GetPeMethodException(string msg)

// 带错误编号的构造函数
public GetPeMethodException(int errorNum, string msg)

// 带内部异常的构造函数
public GetPeMethodException(string msg, Exception innerException)
```

**使用示例：**
```csharp
// PE方法调用异常处理
public void CallPeMethod()
{
    try
    {
        // PE方法调用
        var result = SomePeMethod();
        if (result != ErrorStatus.OK)
        {
            throw new GetPeMethodException((int)result, "PE方法调用失败");
        }
    }
    catch (GetPeMethodException peEx)
    {
        Console.WriteLine($"PE错误 [{peEx.ErrorNum}]: {peEx.ErrorMsg}");
        if (peEx.InnerException1 != null)
        {
            Console.WriteLine($"内部异常: {peEx.InnerException1.Message}");
        }
    }
}
```

### 统一错误处理模式

**推荐的错误处理模式：**
```csharp
public class CadOperationHelper
{
    public static void SafeExecute(Action operation, string operationName = "CAD操作")
    {
        try
        {
            operation();
        }
        catch (AcException acex)
        {
            ErrorInfoEx.AcErrorInfo(acex);
            throw new InvalidOperationException($"{operationName}失败: {acex.Message}", acex);
        }
        catch (GetPeMethodException peEx)
        {
            Console.WriteLine($"PE方法错误 [{peEx.ErrorNum}]: {peEx.ErrorMsg}");
            throw;
        }
        catch (Exception ex)
        {
            Console.WriteLine($"{operationName}发生未知错误: {ex.Message}");
            throw;
        }
    }
}

// 使用示例
CadOperationHelper.SafeExecute(() =>
{
    using (var tr = new DBTrans())
    {
        // 执行CAD操作
        tr.Commit();
    }
}, "数据库事务操作");
```

### 事务管理最佳实践

```csharp
// 始终为数据库操作使用事务
using (var tr = db.TransactionManager.StartTransaction())
{
    try
    {
        // 执行操作
        var entity = tr.GetObject(objectId, OpenMode.ForWrite) as Entity;
        // 修改实体...

        tr.Commit(); // 只有在所有操作成功时才提交
    }
    catch (Exception ex)
    {
        // 事务在异常时自动中止
        // 记录错误或根据需要处理
        throw; // 如果需要，重新抛出
    }
}
```

## 高级使用模式

### 空间查询优化
```csharp
// 为大型实体集创建四叉树
var bounds = new Rect(drawingExtents);
var spatialIndex = new QuadTree<QuadEntity>(bounds);

// 批量插入实体
entities.ForEach(ent => spatialIndex.Insert(new QuadEntity(ent.GeometricExtents)));

// 快速空间查询
var nearbyEntities = spatialIndex.Query(selectionRect, QuadTreeSelectMode.IntersectsWith);
```

### 高效集合处理
```csharp
// 转换 AutoCAD 集合以进行 LINQ 操作
var entityIds = selection.GetObjectIds().ToList();
var entities = entityIds.Select(id => tr.GetObject(id, OpenMode.ForRead)).Cast<Entity>();

// 使用基于容差的去重处理
var uniquePoints = points.Distinct(new TolerancePoint2d(0.001)).ToList();
```

### 安全数据库操作
```csharp
// 自动数据库切换和恢复
using (var dbSwitch = targetDatabase.SwitchDatabase())
using (var tr = targetDatabase.TransactionManager.StartTransaction())
{
    // 在目标数据库上执行操作
    tr.Commit();
} // 数据库自动恢复
```

## 扩展和定制

### 自定义过滤器

```csharp
public class CustomFilter : OpFilter
{
    public override string Name => "CUSTOM";

    public override IEnumerable<TypedValue> ToTypedValues()
    {
        // 实现自定义过滤逻辑
    }
}
```

### 自定义实体扩展

```csharp
public static class MyEntityEx
{
    public static void MyCustomMethod(this Entity entity)
    {
        // 自定义扩展方法
    }
}
```

## 常见开发模式

### 1. 实体创建和管理
```csharp
// 创建实体并添加到模型空间
using (var tr = db.TransactionManager.StartTransaction())
{
    var modelSpace = tr.GetObject(db.CurrentSpaceId, OpenMode.ForWrite) as BlockTableRecord;

    // 创建实体（示例：直线）
    var line = new Line(startPoint, endPoint);

    // 添加到模型空间
    modelSpace.AppendEntity(line);
    tr.AddNewlyCreatedDBObject(line, true);

    tr.Commit();
}
```

### 2. 使用四叉树批量处理实体
```csharp
// 高效处理大量实体
var allEntities = GetAllEntities(); // 您获取实体的方法
var bounds = Rect.GetMinMax(allEntities.Select(e => e.GeometricExtents));
var quadTree = new QuadTree<EntityWrapper>(bounds);

// 索引所有实体
allEntities.ForEach(entity =>
{
    var wrapper = new EntityWrapper(entity);
    quadTree.Insert(wrapper);
});

// 查找特定区域内的实体
var queryRect = new Rect(x1, y1, x2, y2);
var entitiesInRegion = quadTree.Query(queryRect, QuadTreeSelectMode.IntersectsWith);
```

### 3. 与 AutoCAD 命令集成
```csharp
[CommandMethod("MYCOMMAND")]
public void MyCommand()
{
    var doc = Application.DocumentManager.MdiActiveDocument;
    var db = doc.Database;
    var ed = doc.Editor;

    using (var lockDoc = doc.SecurelyLock())
    using (var tr = db.TransactionManager.StartTransaction())
    {
        // 使用 IFoxCAD 扩展
        var selection = ed.SelectAll();
        var entities = selection.Value.GetObjectIds()
            .Select(id => tr.GetObject(id, OpenMode.ForRead))
            .Cast<Entity>()
            .ToList();

        // 使用四叉树处理
        var bounds = Rect.GetMinMax(entities.Select(e => e.GeometricExtents));
        var quadTree = new QuadTree<QuadEntity>(bounds);

        tr.Commit();
    }
}
```

### 4. 自定义实体类
```csharp
public class MyQuadEntity : QuadEntity
{
    public Entity SourceEntity { get; }
    public string CustomProperty { get; set; }

    public MyQuadEntity(Entity entity) : base(entity.GeometricExtents)
    {
        SourceEntity = entity;
        CustomProperty = entity.Layer;
    }
}

// 使用方法
var customQuadTree = new QuadTree<MyQuadEntity>(bounds);
entities.ForEach(e => customQuadTree.Insert(new MyQuadEntity(e)));
```

### 5. 填充操作示例
```csharp
// 创建实体填充
var hatchInfo = new HatchInfo
{
    PatternName = "ANSI31",
    PatternScale = 1.0,
    PatternAngle = 0.0,
    BoundaryIds = boundaryIds
};

using var tr = new DBTrans();
var hatch = hatchInfo.CreateHatch();
tr.CurrentSpace.AddEntity(hatch);

// 创建渐变填充
var gradientInfo = new HatchInfo
{
    IsGradient = true,
    GradientName = GradientName.Linear,
    GradientColors = new[] { Color.Red, Color.Blue },
    BoundaryIds = boundaryIds
};

var gradientHatch = gradientInfo.CreateHatch();
tr.CurrentSpace.AddEntity(gradientHatch);
tr.Commit();
```

### 6. Jig 交互绘图
```csharp
public class LineJig : JigEx
{
    private Line _line;
    private Point3d _startPoint;

    public LineJig(Point3d startPoint)
    {
        _startPoint = startPoint;
        _line = new Line(startPoint, startPoint);
    }

    protected override SamplerStatus Sampler(JigPrompts prompts)
    {
        var options = new JigPromptPointOptions("\n指定终点: ");
        var result = prompts.AcquirePoint(options);

        if (result.Status == PromptStatus.OK)
        {
            _line.EndPoint = result.Value;
            return SamplerStatus.OK;
        }

        return SamplerStatus.Cancel;
    }

    protected override bool Update()
    {
        return true;
    }

    public Entity GetEntity() => _line;
}

// 使用Jig
[CommandMethod("LINEJIG")]
public void LineJigCommand()
{
    var ed = Application.DocumentManager.MdiActiveDocument.Editor;

    var startResult = ed.GetPoint("\n指定起点: ");
    if (startResult.Status != PromptStatus.OK) return;

    var jig = new LineJig(startResult.Value);
    var jigResult = ed.Drag(jig);

    if (jigResult.Status == PromptStatus.OK)
    {
        using var tr = new DBTrans();
        tr.CurrentSpace.AddEntity(jig.GetEntity());
        tr.Commit();
    }
}
```

### 7. 系统变量管理
```csharp
// 使用系统变量管理器
var sysVar = new SystemVariableManager();

// 临时关闭命令回显
var oldCmdecho = sysVar.Cmdecho;
sysVar.Cmdecho = false;

try
{
    // 执行需要静默的操作
    ed.Command("LINE", "0,0", "100,100", "");
}
finally
{
    // 恢复原始设置
    sysVar.Cmdecho = oldCmdecho;
}
```

### 8. 环链表使用
```csharp
// 创建环链表管理顶点
var loopList = new LoopList<Point3d>();
loopList.Add(new Point3d(0, 0, 0));
loopList.Add(new Point3d(100, 0, 0));
loopList.Add(new Point3d(100, 100, 0));
loopList.Add(new Point3d(0, 100, 0));

// 遍历环链表
for (int i = 0; i < loopList.Count * 2; i++) // 遍历两圈
{
    var current = loopList.Current.Value;
    Console.WriteLine($"当前点: {current}");
    loopList.MoveNext();
}
```

## 资源管理和最佳实践

### 1. 资源管理
```csharp
// 正确释放 AutoCAD 集合
var point2dCollection = points.ToCollection();
try
{
    // 使用集合
    polyline.SetPointAt(0, point2dCollection[0]);
}
finally
{
    point2dCollection?.Dispose(); // 始终释放集合
}

// 或在可能时使用 using 语句
using (var collection = points.ToCollection())
{
    // 安全使用集合
}
```

### 2. 容差处理
```csharp
// 对几何操作使用适当的容差
var tolerance = Tolerance.Global.EqualPoint;
var comparer = new TolerancePoint2d(tolerance);

// 删除重复点
var uniquePoints = allPoints.Distinct(comparer).ToList();

// 带容差的矩形操作
var rect1 = new Rect(0, 0, 10, 10);
var rect2 = new Rect(0.0001, 0.0001, 10.0001, 10.0001);
bool areEqual = rect1.Equals(rect2, tolerance);
```

### 3. 性能优化
```csharp
// 对大型数据集的空间操作使用四叉树
if (entityCount > 1000) // 空间索引的阈值
{
    var quadTree = new QuadTree<QuadEntity>(bounds);
    entities.ForEach(e => quadTree.Insert(new QuadEntity(e.GeometricExtents)));

    // 快速空间查询
    var results = quadTree.Query(searchRect, QuadTreeSelectMode.IntersectsWith);
}
else
{
    // 对小数据集使用线性搜索
    var results = entities.Where(e => e.GeometricExtents.IntersectsWith(searchRect));
}
```

## 常见问题排查

### 1. 四叉树性能问题
**问题**: 四叉树操作缓慢
**解决方案**:
- 调整 `QuadTreeEvn.QuadTreeMaximumDepth`（默认值对大多数情况合理）
- 修改 `QuadTreeEvn.QuadTreeContentsCountSplit` 阈值
- 确保 `QuadTreeEvn.MinArea` 适合您的数据规模

### 2. 内存泄漏
**问题**: 内存使用量随时间增加
**解决方案**:
- 始终释放 AutoCAD 集合（`Point2dCollection`、`ObjectIdCollection` 等）
- 对 `DBTrans` 和其他可释放对象使用 `using` 语句
- 正确管理四叉树中的实体引用

### 3. 事务冲突
**问题**: "对象已为写入打开"错误
**解决方案**:
- 使用 `ForWrite()` 扩展方法进行自动升级管理
- 在操作前检查实体打开模式
- 避免对同一实体进行嵌套写操作

### 4. 坐标系问题
**问题**: 几何计算产生意外结果
**解决方案**:
- 确保坐标系一致（WCS vs UCS）
- 对比较使用适当的容差值
- 验证矩形边界正确排序（min < max）

## 版本兼容性说明

### .NET Framework vs .NET 8.0
- **.NET Framework 4.8**: 需要 `IndexRange` 包进行范围操作
- **.NET 8.0**: 原生范围支持，性能更好
- **AutoCAD 版本**: 需要不同的 AutoCAD.NET 包版本

### 从 NFox 迁移
如果从原始 NFox 库迁移：
1. 将命名空间引用从 `NFox` 更新为 `IFoxCAD.Cad`
2. 检查方法签名 - 一些已被简化
3. 更新四叉树使用 - API 已增强
4. 检查扩展方法可用性 - 添加了许多新方法

## 版本信息

- **当前版本：** 0.9.6
- **发布日期：** 2025年5月24日
- **总下载量：** 6.5K+
- **许可证：** 开源

## 项目模板

IFoxCAD 提供了项目模板来快速开始开发：

### VS 模板插件
- 传统的 Visual Studio 项目模板
- 适用于熟悉 VS 模板的开发者

### .NET 项目模板
- 推荐使用的现代项目模板
- 支持 .NET CLI 和现代开发工作流

建议使用 .NET 项目模板来创建新项目，具体使用方法请参考官方文档。

## 使用 IFoxCAD 的几种方式

1. **NuGet 包引用** - 最常用的方式
2. **源码编译** - 用于定制和贡献
3. **项目模板** - 快速开始新项目
4. **示例项目** - 学习和参考

详细信息请参考官方文档中的"使用IFoxCAD的几种方式"章节。

## 库功能完整性统计

基于对 XML 文档的完整分析，IFoxCAD.AutoCAD 库包含以下主要组件：

### 核心命名空间统计
- **IFoxCAD.Cad**: 主要CAD功能，包含100+个类和扩展
- **IFoxCAD.Cad.Assoc**: 关联对象功能，包含关联性API
- **IFoxCAD.Basal**: 基础工具类，包含20+个实用工具类

### 主要功能模块（15个）
1. **空间数据结构** - 四叉树、矩形操作
2. **数据库操作** - 事务管理、字典操作
3. **图形实体扩展** - 所有主要CAD实体的扩展方法
4. **几何计算** - 点、向量、平面操作
5. **用户交互** - 编辑器扩展、选择集操作
6. **系统管理** - 环境变量、自动加载
7. **过滤器系统** - 强大的选择集过滤
8. **数据封装** - 各种数据列表类
9. **填充系统** - 图案填充、渐变填充
10. **符号表管理** - 图层、文字样式、线型管理
11. **Jig交互** - 动态绘图、用户交互
12. **外部参照管理** - 完整的外部参照操作
13. **系统变量管理** - 统一的系统变量接口
14. **窗口和UI扩展** - 窗体、托盘操作
15. **天正接口** - 天正CAD兼容性

### 扩展类统计（50+个主要扩展类）
- **实体扩展**: ArcEx, CircleEx, CurveEx, PolylineEx, DBTextEx, MTextEx, BlockReferenceEx, RegionEx, HatchEx
- **数据库扩展**: DatabaseEx, DBDictionaryEx, DBObjectEx, DBTransEx, TransactionEx
- **编辑器扩展**: EditorEx, SelectionSetEx, JigEx
- **几何扩展**: GeometryEx, Point2dEx, Point3dEx, Vector2dEx, Vector3dEx
- **集合扩展**: CollectionEx, ArrayEx, LinqEx
- **符号表扩展**: SymbolTableEx, LayerTableEx, TextStyleTableEx
- **窗口扩展**: WindowEx, PaneEx
- **外部参照扩展**: XrefEx, XrefFactory

### 工具类统计（30+个工具类）
- **数据结构**: QuadTree, LoopList, Rect, BulgeVertexWidth
- **过滤器**: OpFilter, OpEqual, OpAnd, OpOr, OpNot, OpXor
- **数据列表**: TypedValueList, XDataList, XRecordDataList, LispList
- **系统工具**: SystemVariableManager, Env, AutoRegAssem
- **基础工具**: RandomEx, SystemEx, WindowsAPI, PInvokeUser32

## 总结

IFoxCAD.AutoCAD 是一个功能极其强大且全面的 AutoCAD 二次开发库，它：

- **功能全面**: 涵盖AutoCAD开发的所有主要方面，从基础实体操作到高级系统管理
- **架构清晰**: 15个主要功能模块，50+扩展类，30+工具类，结构层次分明
- **性能优化**: 四叉树空间索引、列扫碰撞检测等高效算法
- **易于使用**: 丰富的扩展方法，简化的API设计，减少样板代码
- **功能强大**: 支持填充、Jig交互、外部参照、系统变量管理等高级功能
- **兼容性好**: 支持多个.NET版本和AutoCAD版本，兼容天正CAD
- **社区活跃**: 完善的中文文档，活跃的QQ群支持

该库不仅简化了 AutoCAD .NET 开发，更提供了企业级的功能完整性和性能保障，是 AutoCAD 二次开发的首选解决方案。无论是简单的实体操作还是复杂的系统集成，IFoxCAD都能提供相应的工具和抽象，大大提高开发效率和代码质量。

## 枚举和常量定义

### 操作模式枚举

#### QuadTreeSelectMode 四叉树选择模式

用于四叉树查询时指定选择条件的枚举。

```csharp
public enum QuadTreeSelectMode
{
    /// <summary>
    /// 碰撞到就选中 - 只要查询区域与实体有任何交集就选中
    /// </summary>
    IntersectsWith,

    /// <summary>
    /// 全包含才选中 - 只有查询区域完全包含实体时才选中
    /// </summary>
    Contains
}
```

**使用示例：**
```csharp
var quadTree = new QuadTree<Entity>(boundary);
var queryRect = new Rect(100, 100, 200, 200);

// 查询与区域相交的所有实体
var intersectingEntities = quadTree.Query(queryRect, QuadTreeSelectMode.IntersectsWith);

// 查询完全包含在区域内的实体
var containedEntities = quadTree.Query(queryRect, QuadTreeSelectMode.Contains);
```

#### QuadTreeFindMode 四叉树查找方向

用于四叉树邻近查找时指定搜索方向的枚举。

```csharp
public enum QuadTreeFindMode
{
    /// <summary>
    /// 上方向查找
    /// </summary>
    Top,

    /// <summary>
    /// 下方向查找
    /// </summary>
    Bottom,

    /// <summary>
    /// 左方向查找
    /// </summary>
    Left,

    /// <summary>
    /// 右方向查找
    /// </summary>
    Right
}
```

**使用示例：**
```csharp
var quadTree = new QuadTree<Entity>(boundary);
var searchRect = new Rect(500, 500, 50, 50);

// 查找上方的邻居实体
var topNeighbors = quadTree.FindNeibor(searchRect, QuadTreeFindMode.Top);

// 查找左侧的邻居实体
var leftNeighbors = quadTree.FindNeibor(searchRect, QuadTreeFindMode.Left);
```

#### RunLispFlag Lisp执行方式

用于指定Lisp代码执行方式的枚举。

```csharp
public enum RunLispFlag
{
    /// <summary>
    /// 使用AdsQueueexpr方式执行
    /// 适用于需要队列执行的场景
    /// </summary>
    AdsQueueexpr,

    /// <summary>
    /// 使用AcedEvaluateLisp方式执行
    /// 适用于立即执行并获取返回值的场景
    /// </summary>
    AcedEvaluateLisp,

    /// <summary>
    /// 使用SendStringToExecute方式执行
    /// 适用于发送命令字符串的场景
    /// </summary>
    SendStringToExecute
}
```

**使用示例：**
```csharp
var editor = Application.DocumentManager.MdiActiveDocument.Editor;

// 使用不同方式执行Lisp代码
EditorEx.RunLisp(editor, "(command \"line\" \"0,0\" \"100,100\" \"\")", RunLispFlag.SendStringToExecute);
EditorEx.RunLisp(editor, "(+ 1 2 3)", RunLispFlag.AcedEvaluateLisp);
EditorEx.RunLisp(editor, "(setq pt (getpoint \"选择点:\"))", RunLispFlag.AdsQueueexpr);
```

#### XrefModes 外部参照模式

用于外部参照操作的模式枚举。

```csharp
public enum XrefModes
{
    /// <summary>
    /// 卸载外部参照
    /// 从当前图形中移除参照，但保持参照定义
    /// </summary>
    Unload,

    /// <summary>
    /// 重载外部参照
    /// 重新加载参照文件的最新版本
    /// </summary>
    Reload,

    /// <summary>
    /// 拆离外部参照
    /// 完全移除参照定义和所有相关数据
    /// </summary>
    Detach,

    /// <summary>
    /// 绑定外部参照
    /// 将参照内容永久合并到当前图形中
    /// </summary>
    Bind
}
```

**使用示例：**
```csharp
// 外部参照管理示例
using (var tr = new DBTrans())
{
    var xrefTable = tr.XrefTable;

    foreach (var xrefId in xrefTable)
    {
        var xrefRecord = tr.GetObject<XrefGraph>(xrefId);

        // 根据需要执行不同的参照操作
        switch (operationMode)
        {
            case XrefModes.Reload:
                // 重载参照
                xrefRecord.Reload();
                break;

            case XrefModes.Unload:
                // 卸载参照
                xrefRecord.Unload();
                break;

            case XrefModes.Bind:
                // 绑定参照
                xrefRecord.Bind();
                break;

            case XrefModes.Detach:
                // 拆离参照
                xrefRecord.Detach();
                break;
        }
    }

    tr.Commit();
}
```

### 系统配置枚举

#### SymModes 符号表模式

用于指定要操作的符号表类型的枚举。

```csharp
public enum SymModes
{
    /// <summary>
    /// 块表 - 管理块定义
    /// </summary>
    BlockTable,

    /// <summary>
    /// 图层表 - 管理图层定义
    /// </summary>
    LayerTable,

    /// <summary>
    /// 文字样式表 - 管理文字样式定义
    /// </summary>
    TextStyleTable,

    /// <summary>
    /// 注册应用程序表 - 管理扩展数据应用程序
    /// </summary>
    RegAppTable,

    /// <summary>
    /// 标注样式表 - 管理标注样式定义
    /// </summary>
    DimStyleTable,

    /// <summary>
    /// 线型表 - 管理线型定义
    /// </summary>
    LinetypeTable,

    /// <summary>
    /// 用户坐标系表 - 管理UCS定义
    /// </summary>
    UcsTable,

    /// <summary>
    /// 视图表 - 管理命名视图
    /// </summary>
    ViewTable,

    /// <summary>
    /// 视口表 - 管理视口配置
    /// </summary>
    ViewportTable,

    /// <summary>
    /// 选项1 - 图层|字体|标注|线型|应用
    /// </summary>
    Option1,

    /// <summary>
    /// 选项2 - 坐标|视口|视图
    /// </summary>
    Option2,

    /// <summary>
    /// 全部符号表
    /// </summary>
    All
}
```

**使用示例：**
```csharp
// 清理未使用的符号表项
using (var tr = new DBTrans())
{
    // 清理未使用的图层
    tr.Database.PurgeSymbolTable(SymModes.LayerTable);

    // 清理未使用的块
    tr.Database.PurgeSymbolTable(SymModes.BlockTable);

    // 清理未使用的文字样式
    tr.Database.PurgeSymbolTable(SymModes.TextStyleTable);

    tr.Commit();
}
```

#### CoordinateSystemCode 坐标系类型

用于指定坐标系转换的源和目标坐标系类型。

```csharp
public enum CoordinateSystemCode
{
    /// <summary>
    /// 世界坐标系 (World Coordinate System)
    /// 固定的全局坐标系
    /// </summary>
    Wcs,

    /// <summary>
    /// 用户坐标系 (User Coordinate System)
    /// 用户定义的坐标系
    /// </summary>
    Ucs,

    /// <summary>
    /// 模型空间坐标系 (Model Space Display Coordinate System)
    /// 模型空间的显示坐标系
    /// </summary>
    MDcs,

    /// <summary>
    /// 图纸空间坐标系 (Paper Space Display Coordinate System)
    /// 图纸空间的显示坐标系
    /// </summary>
    PDcs
}
```

**使用示例：**
```csharp
var editor = Application.DocumentManager.MdiActiveDocument.Editor;

// 获取不同坐标系之间的变换矩阵
var ucsToWcs = EditorEx.GetMatrix(editor, CoordinateSystemCode.Ucs, CoordinateSystemCode.Wcs);
var wcsToUcs = EditorEx.GetMatrix(editor, CoordinateSystemCode.Wcs, CoordinateSystemCode.Ucs);
var mdcsToPdcs = EditorEx.GetMatrix(editor, CoordinateSystemCode.MDcs, CoordinateSystemCode.PDcs);

// 坐标点转换
var ucsPoint = new Point3d(100, 100, 0);
var wcsPoint = ucsPoint.TransformBy(ucsToWcs);

Console.WriteLine($"UCS点: {ucsPoint}");
Console.WriteLine($"WCS点: {wcsPoint}");
```

#### AssemLoadType 程序集加载类型

用于指定AutoCAD插件程序集的加载方式。

```csharp
public enum AssemLoadType
{
    /// <summary>
    /// 启动时加载
    /// AutoCAD启动时自动加载程序集
    /// </summary>
    Starting,

    /// <summary>
    /// 随命令加载
    /// 当调用程序集中的命令时才加载
    /// </summary>
    ByCommand,

    /// <summary>
    /// 禁用加载
    /// 不自动加载程序集
    /// </summary>
    Disabled
}
```

**使用示例：**
```csharp
// 在插件注册时指定加载类型
[assembly: ExtensionApplication(typeof(MyApplication))]
[assembly: CommandClass(typeof(MyCommands))]

public class MyApplication : IExtensionApplication
{
    public void Initialize()
    {
        // 根据加载类型执行不同的初始化逻辑
        var loadType = GetCurrentLoadType();

        switch (loadType)
        {
            case AssemLoadType.Starting:
                // 启动时加载，执行完整初始化
                InitializeFullFeatures();
                break;

            case AssemLoadType.ByCommand:
                // 按需加载，延迟初始化
                InitializeLazyFeatures();
                break;

            case AssemLoadType.Disabled:
                // 禁用状态，不执行初始化
                break;
        }
    }

    private AssemLoadType GetCurrentLoadType()
    {
        // 从注册表或配置文件读取加载类型
        // 这里简化为返回默认值
        return AssemLoadType.ByCommand;
    }
}
```

**实际应用场景：**

**符号表管理应用：**
```csharp
// 符号表清理工具
public class SymbolTableCleaner
{
    public static void CleanUnusedSymbols(Database db, SymModes mode)
    {
        using (var tr = new DBTrans(db))
        {
            switch (mode)
            {
                case SymModes.LayerTable:
                    CleanUnusedLayers(tr);
                    break;

                case SymModes.BlockTable:
                    CleanUnusedBlocks(tr);
                    break;

                case SymModes.TextStyleTable:
                    CleanUnusedTextStyles(tr);
                    break;

                case SymModes.All:
                    CleanAllUnusedSymbols(tr);
                    break;
            }

            tr.Commit();
        }
    }

    private static void CleanUnusedLayers(DBTrans tr)
    {
        var layerTable = tr.LayerTable;
        var layersToDelete = new List<ObjectId>();

        foreach (var layerId in layerTable)
        {
            var layer = tr.GetObject<LayerTableRecord>(layerId);
            if (!layer.IsUsed && layer.Name != "0")
            {
                layersToDelete.Add(layerId);
            }
        }

        foreach (var layerId in layersToDelete)
        {
            var layer = tr.GetObject<LayerTableRecord>(layerId, OpenMode.ForWrite);
            layer.Erase();
        }
    }
}
```

**坐标系转换应用：**
```csharp
// 坐标系转换工具
public class CoordinateConverter
{
    public static Point3d ConvertPoint(Point3d point, CoordinateSystemCode from, CoordinateSystemCode to)
    {
        var editor = Application.DocumentManager.MdiActiveDocument.Editor;
        var matrix = EditorEx.GetMatrix(editor, from, to);
        return point.TransformBy(matrix);
    }

    public static List<Point3d> ConvertPoints(IEnumerable<Point3d> points, CoordinateSystemCode from, CoordinateSystemCode to)
    {
        var editor = Application.DocumentManager.MdiActiveDocument.Editor;
        var matrix = EditorEx.GetMatrix(editor, from, to);

        return points.Select(p => p.TransformBy(matrix)).ToList();
    }

    // 实体坐标系转换
    public static void TransformEntity(Entity entity, CoordinateSystemCode from, CoordinateSystemCode to)
    {
        var matrix = EditorEx.GetMatrix(
            Application.DocumentManager.MdiActiveDocument.Editor,
            from, to);

        entity.TransformBy(matrix);
    }
}
```

**程序集加载管理：**
```csharp
// 插件加载管理器
public class PluginLoadManager
{
    private static readonly Dictionary<string, AssemLoadType> PluginLoadTypes =
        new Dictionary<string, AssemLoadType>();

    public static void RegisterPlugin(string pluginName, AssemLoadType loadType)
    {
        PluginLoadTypes[pluginName] = loadType;

        switch (loadType)
        {
            case AssemLoadType.Starting:
                // 注册为启动时加载
                RegisterForStartupLoad(pluginName);
                break;

            case AssemLoadType.ByCommand:
                // 注册为按需加载
                RegisterForDemandLoad(pluginName);
                break;

            case AssemLoadType.Disabled:
                // 禁用插件
                DisablePlugin(pluginName);
                break;
        }
    }

    private static void RegisterForStartupLoad(string pluginName)
    {
        // 将插件添加到AutoCAD启动加载列表
        // 实现省略
    }

    private static void RegisterForDemandLoad(string pluginName)
    {
        // 将插件注册为按需加载
        // 实现省略
    }

    private static void DisablePlugin(string pluginName)
    {
        // 禁用插件加载
        // 实现省略
    }
}
```

### 错误和状态枚举

#### GetMethodErrorNum PE方法错误编号

用于PE方法调用时的错误状态枚举，对应GetPeMethodException的错误值。

```csharp
public enum GetMethodErrorNum
{
    /// <summary>
    /// 操作成功，无错误
    /// </summary>
    Ok,

    /// <summary>
    /// 未找到模块
    /// 指定的DLL模块不存在或无法加载
    /// </summary>
    NoModule,

    /// <summary>
    /// 未找到函数名
    /// 指定的函数在模块中不存在
    /// </summary>
    NoFuncName
}
```

**使用示例：**
```csharp
try
{
    // 尝试获取PE方法
    var result = AcadPeInfo.GetDelegate<SomeDelegate>("functionName", AcadPeEnum.AcadExe);
    if (result == null)
    {
        throw new GetPeMethodException((int)GetMethodErrorNum.NoFuncName, "未找到指定函数");
    }
}
catch (GetPeMethodException ex)
{
    switch ((GetMethodErrorNum)ex.ErrorNum)
    {
        case GetMethodErrorNum.NoModule:
            Console.WriteLine("模块加载失败");
            break;

        case GetMethodErrorNum.NoFuncName:
            Console.WriteLine("函数不存在");
            break;

        case GetMethodErrorNum.Ok:
            Console.WriteLine("操作成功");
            break;
    }
}
```

#### DBmod 数据库修改状态

用于获取和设置AutoCAD数据库的修改状态标志。

```csharp
public enum DBmod
{
    /// <summary>
    /// 数据库未修改
    /// 图形文件没有任何更改
    /// </summary>
    DatabaseNoModifies,

    /// <summary>
    /// 数据库有修改
    /// 图形文件的实体或对象有更改
    /// </summary>
    Database,

    /// <summary>
    /// 变量有修改
    /// 系统变量或用户变量有更改
    /// </summary>
    Value,

    /// <summary>
    /// 窗口有修改
    /// 窗口布局或显示设置有更改
    /// </summary>
    Window,

    /// <summary>
    /// 视图有修改
    /// 视图设置或视口配置有更改
    /// </summary>
    View,

    /// <summary>
    /// 字段有修改
    /// 字段值或字段定义有更改
    /// </summary>
    Field
}
```

**使用示例：**
```csharp
// 检查数据库修改状态
var currentStatus = DBmodEx.DBmod;
Console.WriteLine($"当前修改状态: {currentStatus}");

// 根据修改状态决定是否保存
switch (currentStatus)
{
    case DBmod.DatabaseNoModifies:
        Console.WriteLine("图形无修改，无需保存");
        break;

    case DBmod.Database:
        Console.WriteLine("图形有修改，建议保存");
        // 执行保存操作
        break;

    case DBmod.Value:
        Console.WriteLine("变量有修改");
        break;

    case DBmod.Window:
        Console.WriteLine("窗口设置有修改");
        break;

    case DBmod.View:
        Console.WriteLine("视图有修改");
        break;

    case DBmod.Field:
        Console.WriteLine("字段有修改");
        break;
}

// 手动设置修改状态
using (var tr = new DBTrans())
{
    var database = tr.Database;

    // 标记数据库为已修改
    DBmodEx.AcdbSetDbmod(database.UnmanagedObject, DBmod.Database);

    // 或者标记为未修改
    DBmodEx.AcdbSetDbmod(database.UnmanagedObject, DBmod.DatabaseNoModifies);

    tr.Commit();
}
```

#### AcadPeEnum PE文件选择模式

用于指定要读取的AutoCAD PE文件类型。

```csharp
public enum AcadPeEnum
{
    /// <summary>
    /// AutoCAD主程序 (acad.exe)
    /// 包含AutoCAD核心功能的主执行文件
    /// </summary>
    AcadExe,

    /// <summary>
    /// AutoCAD核心库 (accore.dll)
    /// 包含AutoCAD核心API的动态链接库
    /// </summary>
    AccoreDll,

    /// <summary>
    /// AutoCAD数据库库 (acdb.dll)
    /// 包含数据库操作相关API的动态链接库
    /// </summary>
    Acdb,

    /// <summary>
    /// 主程序和核心库组合
    /// 同时从acad.exe和accore.dll中查找函数
    /// </summary>
    ExeAndCore
}
```

**使用示例：**
```csharp
// 从不同的PE文件获取函数指针
try
{
    // 从AutoCAD主程序获取函数
    var acadFunction = AcadPeInfo.GetDelegate<SomeDelegate>("functionName", AcadPeEnum.AcadExe);

    // 从核心库获取函数
    var coreFunction = AcadPeInfo.GetDelegate<SomeDelegate>("functionName", AcadPeEnum.AccoreDll);

    // 从数据库库获取函数
    var dbFunction = AcadPeInfo.GetDelegate<SomeDelegate>("functionName", AcadPeEnum.Acdb);

    // 从主程序和核心库组合中查找
    var combinedFunction = AcadPeInfo.GetDelegate<SomeDelegate>("functionName", AcadPeEnum.ExeAndCore);

    if (combinedFunction != null)
    {
        Console.WriteLine("成功获取函数指针");
        // 调用函数
        var result = combinedFunction.Invoke(/* 参数 */);
    }
}
catch (GetPeMethodException ex)
{
    Console.WriteLine($"获取函数失败: {ex.ErrorMsg}");
}
```

**实际应用场景：**

**错误处理和状态监控：**
```csharp
// 综合错误处理和状态监控类
public class CadStatusMonitor
{
    public static void MonitorDatabaseChanges()
    {
        var initialStatus = DBmodEx.DBmod;
        Console.WriteLine($"初始状态: {initialStatus}");

        // 执行一些操作
        using (var tr = new DBTrans())
        {
            // 创建一些实体
            var line = new Line(Point3d.Origin, new Point3d(100, 100, 0));
            tr.CurrentSpace.AddEntity(line);
            tr.Commit();
        }

        var finalStatus = DBmodEx.DBmod;
        Console.WriteLine($"操作后状态: {finalStatus}");

        // 检查状态变化
        if (finalStatus != initialStatus)
        {
            Console.WriteLine("检测到数据库修改");

            // 根据修改类型执行相应操作
            HandleDatabaseModification(finalStatus);
        }
    }

    private static void HandleDatabaseModification(DBmod status)
    {
        switch (status)
        {
            case DBmod.Database:
                // 数据库有修改，提示用户保存
                var result = MessageBox.Show("图形已修改，是否保存？", "提示",
                    MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                if (result == DialogResult.Yes)
                {
                    // 执行保存操作
                    SaveCurrentDrawing();
                }
                break;

            case DBmod.Value:
                Console.WriteLine("系统变量已修改");
                break;

            case DBmod.View:
                Console.WriteLine("视图设置已修改");
                break;
        }
    }

    private static void SaveCurrentDrawing()
    {
        try
        {
            var doc = Application.DocumentManager.MdiActiveDocument;
            doc.Database.SaveAs(doc.Name, DwgVersion.Current);

            // 重置修改状态
            DBmodEx.AcdbSetDbmod(doc.Database.UnmanagedObject, DBmod.DatabaseNoModifies);

            Console.WriteLine("图形保存成功");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"保存失败: {ex.Message}");
        }
    }
}
```

**PE函数动态调用管理：**
```csharp
// PE函数管理器
public class PeFunctionManager
{
    private static readonly Dictionary<string, Delegate> FunctionCache =
        new Dictionary<string, Delegate>();

    public static T GetCachedFunction<T>(string functionName, AcadPeEnum peType) where T : Delegate
    {
        var key = $"{functionName}_{peType}";

        if (FunctionCache.TryGetValue(key, out var cachedFunction))
        {
            return (T)cachedFunction;
        }

        try
        {
            var function = AcadPeInfo.GetDelegate<T>(functionName, peType);
            if (function != null)
            {
                FunctionCache[key] = function;
                return function;
            }
        }
        catch (GetPeMethodException ex)
        {
            LogError(functionName, peType, ex);
        }

        return null;
    }

    private static void LogError(string functionName, AcadPeEnum peType, GetPeMethodException ex)
    {
        var errorType = (GetMethodErrorNum)ex.ErrorNum;
        var peTypeName = peType.ToString();

        switch (errorType)
        {
            case GetMethodErrorNum.NoModule:
                Console.WriteLine($"模块 {peTypeName} 未找到，无法获取函数 {functionName}");
                break;

            case GetMethodErrorNum.NoFuncName:
                Console.WriteLine($"在模块 {peTypeName} 中未找到函数 {functionName}");
                break;

            default:
                Console.WriteLine($"获取函数 {functionName} 时发生未知错误: {ex.ErrorMsg}");
                break;
        }
    }

    // 清理缓存
    public static void ClearCache()
    {
        FunctionCache.Clear();
    }

    // 预加载常用函数
    public static void PreloadCommonFunctions()
    {
        var commonFunctions = new[]
        {
            ("acedCommand", AcadPeEnum.AcadExe),
            ("acedGetPoint", AcadPeEnum.AcadExe),
            ("acdbOpenObject", AcadPeEnum.Acdb)
        };

        foreach (var (funcName, peType) in commonFunctions)
        {
            try
            {
                // 尝试预加载（这里需要具体的委托类型）
                Console.WriteLine($"预加载函数: {funcName} from {peType}");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"预加载函数 {funcName} 失败: {ex.Message}");
            }
        }
    }
}
```

### UI和交互枚举

#### PaneMarginType 托盘边距类型

用于设置AutoCAD托盘面板的边距样式。

```csharp
public enum PaneMarginType
{
    /// <summary>
    /// 无边距
    /// 托盘面板紧贴边缘，无额外空白
    /// </summary>
    NONE,

    /// <summary>
    /// 小边距
    /// 托盘面板有较小的边距空白
    /// </summary>
    SMALL,

    /// <summary>
    /// 大边距
    /// 托盘面板有较大的边距空白
    /// </summary>
    LARGE
}
```

**使用示例：**
```csharp
// 创建自定义托盘面板
public class CustomPaletteSet : PaletteSet
{
    public CustomPaletteSet() : base("自定义工具面板")
    {
        // 设置托盘边距
        SetMarginType(PaneMarginType.SMALL);

        // 添加面板内容
        var userControl = new MyCustomControl();
        Add("工具面板", userControl);

        // 显示面板
        Visible = true;
    }

    private void SetMarginType(PaneMarginType marginType)
    {
        switch (marginType)
        {
            case PaneMarginType.NONE:
                // 设置无边距样式
                this.Dock = DockSides.None;
                break;

            case PaneMarginType.SMALL:
                // 设置小边距样式
                this.MinimumSize = new Size(200, 300);
                break;

            case PaneMarginType.LARGE:
                // 设置大边距样式
                this.MinimumSize = new Size(250, 350);
                break;
        }
    }
}
```

#### SingleKeyWordWorkType 单关键字工作模式

用于指定单关键字输入的工作模式和响应方式。

```csharp
public enum SingleKeyWordWorkType
{
    /// <summary>
    /// ESC模式
    /// 按ESC键退出或取消当前操作
    /// </summary>
    ESCAPE,

    /// <summary>
    /// Enter模式
    /// 按Enter键确认或继续当前操作
    /// </summary>
    ENTER,

    /// <summary>
    /// Write Line模式
    /// 输出信息到命令行
    /// </summary>
    WRITE_LINE
}
```

**使用示例：**
```csharp
// 单关键字输入处理器
public class SingleKeywordHandler
{
    public static void HandleKeywordInput(string keyword, SingleKeyWordWorkType workType)
    {
        switch (workType)
        {
            case SingleKeyWordWorkType.ESCAPE:
                HandleEscapeMode(keyword);
                break;

            case SingleKeyWordWorkType.ENTER:
                HandleEnterMode(keyword);
                break;

            case SingleKeyWordWorkType.WRITE_LINE:
                HandleWriteLineMode(keyword);
                break;
        }
    }

    private static void HandleEscapeMode(string keyword)
    {
        if (keyword.ToUpper() == "ESC" || keyword == "\x1B")
        {
            // 取消当前操作
            var editor = Application.DocumentManager.MdiActiveDocument.Editor;
            editor.WriteMessage("\n操作已取消。");

            // 发送ESC命令
            Application.DocumentManager.MdiActiveDocument.SendStringToExecute("\x1B", true, false, false);
        }
    }

    private static void HandleEnterMode(string keyword)
    {
        if (keyword == "\r" || keyword == "\n" || string.IsNullOrEmpty(keyword))
        {
            // 确认当前操作
            var editor = Application.DocumentManager.MdiActiveDocument.Editor;
            editor.WriteMessage("\n操作已确认。");
        }
    }

    private static void HandleWriteLineMode(string keyword)
    {
        // 输出关键字到命令行
        var editor = Application.DocumentManager.MdiActiveDocument.Editor;
        editor.WriteMessage($"\n接收到关键字: {keyword}");
    }
}

// 在命令中使用单关键字处理
[CommandMethod("TESTKEYWORD")]
public void TestKeywordCommand()
{
    var editor = Application.DocumentManager.MdiActiveDocument.Editor;

    var options = new PromptKeywordOptions("\n选择操作模式 [ESC退出(E)/确认(C)/输出(W)]:")
    {
        AllowNone = false
    };
    options.Keywords.Add("E");
    options.Keywords.Add("C");
    options.Keywords.Add("W");

    var result = editor.GetKeywords(options);
    if (result.Status == PromptStatus.OK)
    {
        switch (result.StringResult.ToUpper())
        {
            case "E":
                SingleKeywordHandler.HandleKeywordInput("ESC", SingleKeyWordWorkType.ESCAPE);
                break;
            case "C":
                SingleKeywordHandler.HandleKeywordInput("", SingleKeyWordWorkType.ENTER);
                break;
            case "W":
                SingleKeywordHandler.HandleKeywordInput("测试输出", SingleKeyWordWorkType.WRITE_LINE);
                break;
        }
    }
}
```

#### FontTTF 字体类型枚举

用于指定AutoCAD中常用的TTF字体类型。

```csharp
public enum FontTTF
{
    /// <summary>
    /// 宋体 - 中文标准字体
    /// </summary>
    宋体,

    /// <summary>
    /// 仿宋 - 中文仿宋字体
    /// </summary>
    仿宋,

    /// <summary>
    /// 仿宋GB2312 - GB2312编码的仿宋字体
    /// </summary>
    仿宋GB2312,

    /// <summary>
    /// Arial - 英文无衬线字体
    /// </summary>
    Arial,

    /// <summary>
    /// Romans - AutoCAD标准英文字体
    /// </summary>
    Romans
}
```

**使用示例：**
```csharp
// 字体管理工具
public class FontManager
{
    public static string GetFontName(FontTTF fontType)
    {
        switch (fontType)
        {
            case FontTTF.宋体:
                return "SimSun";
            case FontTTF.仿宋:
                return "FangSong";
            case FontTTF.仿宋GB2312:
                return "FangSong_GB2312";
            case FontTTF.Arial:
                return "Arial";
            case FontTTF.Romans:
                return "romans.shx";
            default:
                return "Arial";
        }
    }

    public static void CreateTextWithFont(Point3d position, string text, FontTTF fontType, double height = 2.5)
    {
        using (var tr = new DBTrans())
        {
            // 获取或创建文字样式
            var textStyleName = $"Style_{fontType}";
            var textStyleId = GetOrCreateTextStyle(tr, textStyleName, fontType);

            // 创建文字对象
            var dbText = new DBText
            {
                Position = position,
                TextString = text,
                Height = height,
                TextStyleId = textStyleId
            };

            tr.CurrentSpace.AddEntity(dbText);
            tr.Commit();
        }
    }

    private static ObjectId GetOrCreateTextStyle(DBTrans tr, string styleName, FontTTF fontType)
    {
        var textStyleTable = tr.TextStyleTable;

        // 检查样式是否已存在
        if (textStyleTable.Has(styleName))
        {
            return textStyleTable[styleName];
        }

        // 创建新的文字样式
        var textStyleRecord = new TextStyleTableRecord
        {
            Name = styleName,
            FileName = GetFontName(fontType),
            TextSize = 0.0, // 0表示可变高度
            XScale = 1.0,
            ObliquingAngle = 0.0
        };

        // 设置字体文件
        if (fontType == FontTTF.Romans)
        {
            textStyleRecord.FileName = "romans.shx";
            textStyleRecord.BigFontFileName = "";
        }
        else
        {
            textStyleRecord.FileName = "txt.shx";
            textStyleRecord.BigFontFileName = GetFontName(fontType) + ".ttf";
        }

        textStyleTable.UpgradeOpen();
        var styleId = textStyleTable.Add(textStyleRecord);
        tr.AddNewlyCreatedDBObject(textStyleRecord, true);

        return styleId;
    }
}

// 使用示例
[CommandMethod("CREATETEXT")]
public void CreateTextCommand()
{
    var editor = Application.DocumentManager.MdiActiveDocument.Editor;

    // 获取插入点
    var pointResult = editor.GetPoint("\n指定文字插入点:");
    if (pointResult.Status != PromptStatus.OK) return;

    // 获取文字内容
    var textResult = editor.GetString("\n输入文字内容:");
    if (textResult.Status != PromptStatus.OK) return;

    // 创建不同字体的文字
    var fonts = new[] { FontTTF.宋体, FontTTF.Arial, FontTTF.Romans };
    var basePoint = pointResult.Value;

    for (int i = 0; i < fonts.Length; i++)
    {
        var position = new Point3d(basePoint.X, basePoint.Y - i * 5, basePoint.Z);
        FontManager.CreateTextWithFont(position, $"{textResult.StringResult} ({fonts[i]})", fonts[i]);
    }

    editor.WriteMessage($"\n已创建 {fonts.Length} 种字体的文字。");
}
```

**实际应用场景：**

**UI界面定制：**
```csharp
// AutoCAD界面定制管理器
public class UICustomizationManager
{
    public static void CreateCustomPalette(PaneMarginType marginType)
    {
        var paletteSet = new PaletteSet("工程工具箱")
        {
            Style = PaletteSetStyles.ShowAutoHideButton |
                   PaletteSetStyles.ShowCloseButton |
                   PaletteSetStyles.Snappable,
            MinimumSize = GetMinimumSize(marginType),
            DockEnabled = DockSides.Left | DockSides.Right
        };

        // 根据边距类型调整布局
        var userControl = CreateToolboxControl(marginType);
        paletteSet.Add("工具", userControl);

        paletteSet.Visible = true;
    }

    private static Size GetMinimumSize(PaneMarginType marginType)
    {
        switch (marginType)
        {
            case PaneMarginType.NONE:
                return new Size(180, 250);
            case PaneMarginType.SMALL:
                return new Size(200, 280);
            case PaneMarginType.LARGE:
                return new Size(250, 320);
            default:
                return new Size(200, 280);
        }
    }

    private static UserControl CreateToolboxControl(PaneMarginType marginType)
    {
        var control = new UserControl();

        // 根据边距类型设置控件间距
        var margin = GetControlMargin(marginType);
        control.Padding = new Padding(margin);

        // 添加工具按钮
        AddToolButtons(control, margin);

        return control;
    }

    private static int GetControlMargin(PaneMarginType marginType)
    {
        switch (marginType)
        {
            case PaneMarginType.NONE: return 2;
            case PaneMarginType.SMALL: return 5;
            case PaneMarginType.LARGE: return 10;
            default: return 5;
        }
    }
}
```

**交互式命令处理：**
```csharp
// 交互式命令处理器
public class InteractiveCommandProcessor
{
    public static void ProcessInteractiveCommand(SingleKeyWordWorkType workType)
    {
        var editor = Application.DocumentManager.MdiActiveDocument.Editor;

        while (true)
        {
            var options = new PromptKeywordOptions("\n选择操作 [绘制(D)/编辑(E)/退出(X)]:")
            {
                AllowNone = true
            };
            options.Keywords.Add("D");
            options.Keywords.Add("E");
            options.Keywords.Add("X");

            var result = editor.GetKeywords(options);

            if (result.Status == PromptStatus.Cancel ||
                (result.Status == PromptStatus.OK && result.StringResult.ToUpper() == "X"))
            {
                SingleKeywordHandler.HandleKeywordInput("ESC", SingleKeyWordWorkType.ESCAPE);
                break;
            }

            if (result.Status == PromptStatus.OK)
            {
                switch (result.StringResult.ToUpper())
                {
                    case "D":
                        ProcessDrawCommand(workType);
                        break;
                    case "E":
                        ProcessEditCommand(workType);
                        break;
                }
            }
            else if (result.Status == PromptStatus.None)
            {
                // 处理空输入（Enter键）
                SingleKeywordHandler.HandleKeywordInput("", SingleKeyWordWorkType.ENTER);
                continue;
            }
        }
    }

    private static void ProcessDrawCommand(SingleKeyWordWorkType workType)
    {
        SingleKeywordHandler.HandleKeywordInput("开始绘制操作", SingleKeyWordWorkType.WRITE_LINE);
        // 执行绘制逻辑
    }

    private static void ProcessEditCommand(SingleKeyWordWorkType workType)
    {
        SingleKeywordHandler.HandleKeywordInput("开始编辑操作", SingleKeyWordWorkType.WRITE_LINE);
        // 执行编辑逻辑
    }
}
```

### 常量和配置项

#### QuadTreeEvn 四叉树环境变量

四叉树的全局配置参数，用于控制四叉树的性能和行为。

```csharp
public static class QuadTreeEvn
{
    /// <summary>
    /// 最小的节点面积（一定要大于0）
    /// 当节点面积小于此值时，不再进行分裂
    /// 默认值：1.0
    /// </summary>
    public static double MinArea { get; set; } = 1.0;

    /// <summary>
    /// 选择模式
    /// 默认的四叉树查询选择模式
    /// 默认值：QuadTreeSelectMode.IntersectsWith
    /// </summary>
    public static QuadTreeSelectMode SelectMode { get; set; } = QuadTreeSelectMode.IntersectsWith;

    /// <summary>
    /// 四叉树最大深度
    /// 限制四叉树的最大层级，防止过度分裂
    /// 默认值：10
    /// </summary>
    public static int QuadTreeMaximumDepth { get; set; } = 10;

    /// <summary>
    /// 节点内容超过此数量就分裂
    /// 当节点包含的对象数量超过此值时，触发节点分裂
    /// 默认值：10
    /// </summary>
    public static int QuadTreeContentsCountSplit { get; set; } = 10;
}
```

**配置说明：**

**MinArea（最小节点面积）：**
- **作用**：控制四叉树节点的最小尺寸
- **影响**：值越小，四叉树分裂越细致，查询精度越高，但内存消耗增加
- **建议**：根据实体的平均尺寸设置，通常为实体最小尺寸的1/4

**SelectMode（选择模式）：**
- **作用**：设置默认的查询模式
- **选项**：
  - `IntersectsWith`：相交即选中（适合快速查询）
  - `Contains`：完全包含才选中（适合精确查询）

**QuadTreeMaximumDepth（最大深度）：**
- **作用**：限制四叉树的层级深度
- **影响**：深度越大，分裂越细致，但构建时间增加
- **建议**：一般设置为8-15层，根据数据密度调整

**QuadTreeContentsCountSplit（分裂阈值）：**
- **作用**：控制节点分裂的触发条件
- **影响**：值越小，分裂越频繁，查询速度越快，但内存消耗增加
- **建议**：根据实体数量和查询频率设置，通常为5-20

**使用示例：**

**基本配置：**
```csharp
// 配置四叉树环境变量
public static void ConfigureQuadTree()
{
    // 设置最小节点面积（适合小尺寸实体）
    QuadTreeEvn.MinArea = 0.5;

    // 设置默认选择模式为相交选择
    QuadTreeEvn.SelectMode = QuadTreeSelectMode.IntersectsWith;

    // 设置最大深度为12层
    QuadTreeEvn.QuadTreeMaximumDepth = 12;

    // 设置分裂阈值为15个对象
    QuadTreeEvn.QuadTreeContentsCountSplit = 15;

    Console.WriteLine("四叉树环境变量配置完成");
    Console.WriteLine($"最小面积: {QuadTreeEvn.MinArea}");
    Console.WriteLine($"选择模式: {QuadTreeEvn.SelectMode}");
    Console.WriteLine($"最大深度: {QuadTreeEvn.QuadTreeMaximumDepth}");
    Console.WriteLine($"分裂阈值: {QuadTreeEvn.QuadTreeContentsCountSplit}");
}
```

**性能优化配置：**
```csharp
// 根据不同场景优化四叉树配置
public class QuadTreeOptimizer
{
    // 高精度配置（适合精密绘图）
    public static void ConfigureForHighPrecision()
    {
        QuadTreeEvn.MinArea = 0.1;              // 更小的最小面积
        QuadTreeEvn.QuadTreeMaximumDepth = 15;   // 更深的层级
        QuadTreeEvn.QuadTreeContentsCountSplit = 5; // 更小的分裂阈值
        QuadTreeEvn.SelectMode = QuadTreeSelectMode.Contains; // 精确选择

        Console.WriteLine("已配置为高精度模式");
    }

    // 高性能配置（适合大量实体）
    public static void ConfigureForHighPerformance()
    {
        QuadTreeEvn.MinArea = 2.0;              // 较大的最小面积
        QuadTreeEvn.QuadTreeMaximumDepth = 8;    // 较浅的层级
        QuadTreeEvn.QuadTreeContentsCountSplit = 20; // 较大的分裂阈值
        QuadTreeEvn.SelectMode = QuadTreeSelectMode.IntersectsWith; // 快速选择

        Console.WriteLine("已配置为高性能模式");
    }

    // 平衡配置（默认推荐）
    public static void ConfigureForBalance()
    {
        QuadTreeEvn.MinArea = 1.0;              // 平衡的最小面积
        QuadTreeEvn.QuadTreeMaximumDepth = 10;   // 平衡的层级
        QuadTreeEvn.QuadTreeContentsCountSplit = 10; // 平衡的分裂阈值
        QuadTreeEvn.SelectMode = QuadTreeSelectMode.IntersectsWith; // 通用选择

        Console.WriteLine("已配置为平衡模式");
    }

    // 根据实体数量自动配置
    public static void AutoConfigure(int entityCount)
    {
        if (entityCount < 1000)
        {
            ConfigureForHighPrecision();
        }
        else if (entityCount > 10000)
        {
            ConfigureForHighPerformance();
        }
        else
        {
            ConfigureForBalance();
        }

        Console.WriteLine($"根据实体数量 {entityCount} 自动配置完成");
    }
}
```

**动态配置管理：**
```csharp
// 四叉树配置管理器
public class QuadTreeConfigManager
{
    private static readonly Dictionary<string, QuadTreeConfig> Profiles =
        new Dictionary<string, QuadTreeConfig>();

    public struct QuadTreeConfig
    {
        public double MinArea;
        public QuadTreeSelectMode SelectMode;
        public int MaxDepth;
        public int SplitCount;

        public QuadTreeConfig(double minArea, QuadTreeSelectMode selectMode,
                             int maxDepth, int splitCount)
        {
            MinArea = minArea;
            SelectMode = selectMode;
            MaxDepth = maxDepth;
            SplitCount = splitCount;
        }
    }

    static QuadTreeConfigManager()
    {
        // 预定义配置文件
        Profiles["Default"] = new QuadTreeConfig(1.0, QuadTreeSelectMode.IntersectsWith, 10, 10);
        Profiles["HighPrecision"] = new QuadTreeConfig(0.1, QuadTreeSelectMode.Contains, 15, 5);
        Profiles["HighPerformance"] = new QuadTreeConfig(2.0, QuadTreeSelectMode.IntersectsWith, 8, 20);
        Profiles["LargeScale"] = new QuadTreeConfig(5.0, QuadTreeSelectMode.IntersectsWith, 6, 50);
        Profiles["SmallScale"] = new QuadTreeConfig(0.05, QuadTreeSelectMode.Contains, 20, 3);
    }

    public static void ApplyProfile(string profileName)
    {
        if (Profiles.TryGetValue(profileName, out var config))
        {
            QuadTreeEvn.MinArea = config.MinArea;
            QuadTreeEvn.SelectMode = config.SelectMode;
            QuadTreeEvn.QuadTreeMaximumDepth = config.MaxDepth;
            QuadTreeEvn.QuadTreeContentsCountSplit = config.SplitCount;

            Console.WriteLine($"已应用配置文件: {profileName}");
            LogCurrentConfig();
        }
        else
        {
            Console.WriteLine($"配置文件 {profileName} 不存在");
        }
    }

    public static void SaveCurrentAsProfile(string profileName)
    {
        var config = new QuadTreeConfig(
            QuadTreeEvn.MinArea,
            QuadTreeEvn.SelectMode,
            QuadTreeEvn.QuadTreeMaximumDepth,
            QuadTreeEvn.QuadTreeContentsCountSplit
        );

        Profiles[profileName] = config;
        Console.WriteLine($"当前配置已保存为: {profileName}");
    }

    public static void ListProfiles()
    {
        Console.WriteLine("可用的配置文件:");
        foreach (var profile in Profiles)
        {
            var config = profile.Value;
            Console.WriteLine($"  {profile.Key}: MinArea={config.MinArea}, " +
                            $"Mode={config.SelectMode}, Depth={config.MaxDepth}, " +
                            $"Split={config.SplitCount}");
        }
    }

    private static void LogCurrentConfig()
    {
        Console.WriteLine("当前四叉树配置:");
        Console.WriteLine($"  最小面积: {QuadTreeEvn.MinArea}");
        Console.WriteLine($"  选择模式: {QuadTreeEvn.SelectMode}");
        Console.WriteLine($"  最大深度: {QuadTreeEvn.QuadTreeMaximumDepth}");
        Console.WriteLine($"  分裂阈值: {QuadTreeEvn.QuadTreeContentsCountSplit}");
    }
}

// 使用示例
[CommandMethod("QTCONFIG")]
public void QuadTreeConfigCommand()
{
    var editor = Application.DocumentManager.MdiActiveDocument.Editor;

    // 列出可用配置
    QuadTreeConfigManager.ListProfiles();

    // 获取用户选择
    var options = new PromptKeywordOptions("\n选择配置文件 [默认(D)/高精度(H)/高性能(P)/大比例(L)/小比例(S)]:")
    {
        AllowNone = false
    };
    options.Keywords.Add("D");
    options.Keywords.Add("H");
    options.Keywords.Add("P");
    options.Keywords.Add("L");
    options.Keywords.Add("S");

    var result = editor.GetKeywords(options);
    if (result.Status == PromptStatus.OK)
    {
        switch (result.StringResult.ToUpper())
        {
            case "D":
                QuadTreeConfigManager.ApplyProfile("Default");
                break;
            case "H":
                QuadTreeConfigManager.ApplyProfile("HighPrecision");
                break;
            case "P":
                QuadTreeConfigManager.ApplyProfile("HighPerformance");
                break;
            case "L":
                QuadTreeConfigManager.ApplyProfile("LargeScale");
                break;
            case "S":
                QuadTreeConfigManager.ApplyProfile("SmallScale");
                break;
        }
    }
}
```

**配置最佳实践：**

1. **根据图形规模选择配置**：
   - 小图形（<1000实体）：使用高精度配置
   - 中等图形（1000-10000实体）：使用平衡配置
   - 大图形（>10000实体）：使用高性能配置

2. **根据操作类型调整**：
   - 精确选择操作：使用Contains模式
   - 快速查询操作：使用IntersectsWith模式

3. **内存和性能权衡**：
   - 内存充足：可以降低MinArea和SplitCount
   - 内存紧张：适当增加MinArea和SplitCount

4. **动态调整**：
   - 在程序启动时根据硬件配置自动选择
   - 在处理不同类型图形时动态切换配置

## API 参考手册

### IFoxCAD.Cad 命名空间

#### 核心类 (Core Classes)

**事务和数据库管理**
- [`DBTrans`](#事务管理-dbtrans) - 事务栈管理，简化数据库操作
- [`DatabaseEx`](#数据库扩展-databaseex) - 数据库扩展方法
- [`SwitchDatabase`](#数据库切换-switchdatabase) - 自动切换活动数据库
- [`DocumentLockManager`](#文档锁管理器-documentlockmanager) - 文档锁管理器
- [`DocumentLockManagerExtension`](#文档锁管理器-documentlockmanager) - 文档锁管理扩展

**实体操作类**
- [`EntityEx`](#实体操作-entityex) - 实体扩展方法（移动、旋转、缩放、镜像）
- [`ArcEx`](#实体操作-entityex) - 圆弧扩展方法
- [`CircleEx`](#实体操作-entityex) - 圆扩展方法
- [`PolylineEx`](#实体操作-entityex) - 多段线扩展方法
- [`HatchEx`](#填充扩展-hatchex) - 填充扩展方法
- [`RegionEx`](#实体操作-entityex) - 面域扩展方法

**编辑器和用户交互**
- [`EditorEx`](#编辑器扩展-editorex) - 编辑器扩展方法（选择、输入、视图控制）
- [`SelectionSetEx`](#选择集扩展-selectionsetex) - 选择集扩展方法
- [`JigEx`](#夹点操作-jigex) - 夹点操作扩展

**空间数据结构**
- [`QuadTree<T>`](#四叉树-quadtree) - 四叉树空间索引
- [`QuadTreeNode<T>`](#四叉树-quadtree) - 四叉树节点
- [`QuadEntity`](#四叉树-quadtree) - 四叉树图元

**文件和标记管理**
- [`DwgMark`](#dwg文件标记管理-dwgmark) - DWG文件标记管理
- [`PeInfo`](#pe文件信息分析系统) - PE文件信息分析
- [`AcadPeInfo`](#pe文件信息分析系统) - AutoCAD专用PE信息

**关联功能**
- [`AssocPersSubentityIdPEEx`](#关联子实体扩展-assocperssubentityidpeex) - 关联子实体扩展
- [`AssocUtils`](#关联动作工具-assocutils) - 关联动作工具

**错误处理**
- [`ErrorInfoEx`](#cad错误信息处理-errorinfoex) - CAD错误信息处理
- [`GetPeMethodException`](#pe方法专用异常类) - PE方法专用异常

#### 枚举类型 (Enumerations)

**操作模式枚举**
- [`QuadTreeSelectMode`](#quadtreeselectmode-四叉树选择模式) - 四叉树选择模式
- [`QuadTreeFindMode`](#quadtreefindmode-四叉树查找方向) - 四叉树查找方向
- [`RunLispFlag`](#runlispflag-lisp执行方式) - Lisp执行方式
- [`XrefModes`](#xrefmodes-外部参照模式) - 外部参照模式

**系统配置枚举**
- [`SymModes`](#symmodes-符号表模式) - 符号表模式
- [`CoordinateSystemCode`](#coordinatesystemcode-坐标系类型) - 坐标系类型
- [`AssemLoadType`](#assemloadtype-程序集加载类型) - 程序集加载类型

**错误和状态枚举**
- [`GetMethodErrorNum`](#getmethoderrornum-pe方法错误编号) - PE方法错误编号
- [`DBmod`](#dbmod-数据库修改状态) - 数据库修改状态
- [`AcadPeEnum`](#acadpeenum-pe文件选择模式) - PE文件选择模式

**UI和交互枚举**
- [`PaneMarginType`](#panemargintype-托盘边距类型) - 托盘边距类型
- [`SingleKeyWordWorkType`](#singlekeywordworktype-单关键字工作模式) - 单关键字工作模式
- [`FontTTF`](#fontttf-字体类型枚举) - 字体类型枚举

#### 配置类 (Configuration)

- [`QuadTreeEvn`](#quadtreeevn-四叉树环境变量) - 四叉树环境变量配置

### IFoxCAD.Basal 命名空间

#### 集合和数据结构扩展

**数组和LINQ扩展**
- [`ArrayEx`](#arrayex-数组扩展类) - 数组操作扩展（合并、去重）
- [`LinqEx`](#linqex-linq扩展类) - LINQ扩展（查找最值、排序）

**环形数据结构**
- [`LoopList<T>`](#looplist-环链表类) - 环形双向链表
- [`LoopListNode<T>`](#looplist-环链表类) - 环链表节点

#### 系统API封装

**Windows API封装**
- [`PInvokeUser32`](#pinvokeuser32-系统api封装类) - User32.dll API封装
- [`WindowsAPI`](#windowsapi-系统工具类) - 系统工具类（内存管理、数据转换）

#### 工具类

**随机数和系统扩展**
- [`RandomEx`](#randomex-随机数扩展类) - 随机数生成扩展
- [`SystemEx`](#systemex-系统扩展类) - 系统操作扩展

**调试和验证工具**
- [`DebugEx`](#debugex-调试工具类) - 调试工具（性能测量、内存监控）
- [`EnumEx`](#enumex-枚举扩展类) - 枚举操作扩展
- [`ArgumentNullEx`](#argumentnullex-参数验证类) - 参数验证工具

### 快速查找索引

#### 按功能分类

**🏗️ 基础设施**
- 事务管理：[DBTrans](#事务管理-dbtrans)
- 数据库操作：[DatabaseEx](#数据库扩展-databaseex)
- 文档锁定：[DocumentLockManager](#文档锁管理器-documentlockmanager)

**📐 实体操作**
- 通用实体：[EntityEx](#实体操作-entityex)
- 圆弧操作：[ArcEx](#实体操作-entityex)
- 圆形操作：[CircleEx](#实体操作-entityex)
- 多段线：[PolylineEx](#实体操作-entityex)
- 填充操作：[HatchEx](#填充扩展-hatchex)

**🖱️ 用户交互**
- 编辑器扩展：[EditorEx](#编辑器扩展-editorex)
- 选择操作：[SelectionSetEx](#选择集扩展-selectionsetex)
- 夹点操作：[JigEx](#夹点操作-jigex)

**🔍 空间查询**
- 四叉树：[QuadTree](#四叉树-quadtree)
- 空间索引：[QuadEntity](#四叉树-quadtree)

**📁 文件处理**
- DWG标记：[DwgMark](#dwg文件标记管理-dwgmark)
- PE分析：[PeInfo](#pe文件信息分析系统)

**🔗 关联功能**
- 子实体：[AssocPersSubentityIdPEEx](#关联子实体扩展-assocperssubentityidpeex)
- 关联动作：[AssocUtils](#关联动作工具-assocutils)

**⚠️ 错误处理**
- 错误信息：[ErrorInfoEx](#cad错误信息处理-errorinfoex)
- PE异常：[GetPeMethodException](#pe方法专用异常类)

**🛠️ 工具类**
- 数组操作：[ArrayEx](#arrayex-数组扩展类)
- LINQ扩展：[LinqEx](#linqex-linq扩展类)
- 环链表：[LoopList](#looplist-环链表类)
- 系统API：[PInvokeUser32](#pinvokeuser32-系统api封装类)
- 调试工具：[DebugEx](#debugex-调试工具类)

#### 按字母顺序

**A-C**
- [AcadPeInfo](#pe文件信息分析系统)
- [AcadPeEnum](#acadpeenum-pe文件选择模式)
- [ArcEx](#实体操作-entityex)
- [ArgumentNullEx](#argumentnullex-参数验证类)
- [ArrayEx](#arrayex-数组扩展类)
- [AssemLoadType](#assemloadtype-程序集加载类型)
- [AssocPersSubentityIdPEEx](#关联子实体扩展-assocperssubentityidpeex)
- [AssocUtils](#关联动作工具-assocutils)
- [CircleEx](#实体操作-entityex)
- [CoordinateSystemCode](#coordinatesystemcode-坐标系类型)

**D-H**
- [DatabaseEx](#数据库扩展-databaseex)
- [DBmod](#dbmod-数据库修改状态)
- [DBTrans](#事务管理-dbtrans)
- [DebugEx](#debugex-调试工具类)
- [DocumentLockManager](#文档锁管理器-documentlockmanager)
- [DwgMark](#dwg文件标记管理-dwgmark)
- [EditorEx](#编辑器扩展-editorex)
- [EntityEx](#实体操作-entityex)
- [EnumEx](#enumex-枚举扩展类)
- [ErrorInfoEx](#cad错误信息处理-errorinfoex)
- [FontTTF](#fontttf-字体类型枚举)
- [GetMethodErrorNum](#getmethoderrornum-pe方法错误编号)
- [GetPeMethodException](#pe方法专用异常类)
- [HatchEx](#填充扩展-hatchex)

**J-P**
- [JigEx](#夹点操作-jigex)
- [LinqEx](#linqex-linq扩展类)
- [LoopList](#looplist-环链表类)
- [PaneMarginType](#panemargintype-托盘边距类型)
- [PeInfo](#pe文件信息分析系统)
- [PInvokeUser32](#pinvokeuser32-系统api封装类)
- [PolylineEx](#实体操作-entityex)

**Q-Z**
- [QuadEntity](#四叉树-quadtree)
- [QuadTree](#四叉树-quadtree)
- [QuadTreeEvn](#quadtreeevn-四叉树环境变量)
- [QuadTreeFindMode](#quadtreefindmode-四叉树查找方向)
- [QuadTreeSelectMode](#quadtreeselectmode-四叉树选择模式)
- [RandomEx](#randomex-随机数扩展类)
- [RegionEx](#实体操作-entityex)
- [RunLispFlag](#runlispflag-lisp执行方式)
- [SelectionSetEx](#选择集扩展-selectionsetex)
- [SingleKeyWordWorkType](#singlekeywordworktype-单关键字工作模式)
- [SwitchDatabase](#数据库切换-switchdatabase)
- [SymModes](#symmodes-符号表模式)
- [SystemEx](#systemex-系统扩展类)
- [WindowsAPI](#windowsapi-系统工具类)
- [XrefModes](#xrefmodes-外部参照模式)

## 最佳实践

### 性能优化建议

#### 1. 事务管理优化

**推荐做法：**
```csharp
// ✅ 推荐：使用DBTrans进行批量操作
using (var tr = new DBTrans())
{
    // 批量创建实体
    for (int i = 0; i < 1000; i++)
    {
        var line = new Line(new Point3d(i, 0, 0), new Point3d(i, 100, 0));
        tr.CurrentSpace.AddEntity(line);
    }
    tr.Commit(); // 一次性提交所有操作
}
```

**避免做法：**
```csharp
// ❌ 避免：频繁的事务开启和提交
for (int i = 0; i < 1000; i++)
{
    using (var tr = new DBTrans()) // 每次循环都创建新事务
    {
        var line = new Line(new Point3d(i, 0, 0), new Point3d(i, 100, 0));
        tr.CurrentSpace.AddEntity(line);
        tr.Commit(); // 频繁提交影响性能
    }
}
```

#### 2. 四叉树配置优化

**根据数据规模调整配置：**
```csharp
// 大量实体场景（>10000个）
public static void ConfigureForLargeDataset()
{
    QuadTreeEvn.MinArea = 5.0;                    // 较大的最小面积
    QuadTreeEvn.QuadTreeMaximumDepth = 8;         // 较浅的深度
    QuadTreeEvn.QuadTreeContentsCountSplit = 50;  // 较大的分裂阈值
}

// 精密操作场景（<1000个）
public static void ConfigureForPrecision()
{
    QuadTreeEvn.MinArea = 0.1;                    // 较小的最小面积
    QuadTreeEvn.QuadTreeMaximumDepth = 15;        // 较深的深度
    QuadTreeEvn.QuadTreeContentsCountSplit = 5;   // 较小的分裂阈值
}
```

#### 3. 内存管理

**及时释放资源：**
```csharp
// ✅ 推荐：使用using语句自动释放
using (var tr = new DBTrans())
{
    // 操作代码
    tr.Commit();
} // 自动释放资源

// ✅ 推荐：大量数据处理时分批处理
public void ProcessLargeDataset(IEnumerable<ObjectId> entityIds)
{
    const int batchSize = 1000;
    var batches = entityIds.Batch(batchSize);

    foreach (var batch in batches)
    {
        using (var tr = new DBTrans())
        {
            foreach (var id in batch)
            {
                var entity = tr.GetObject<Entity>(id, OpenMode.ForWrite);
                // 处理实体
            }
            tr.Commit();
        }

        // 强制垃圾回收（仅在必要时）
        if (batches.Count() > 10)
        {
            GC.Collect();
            GC.WaitForPendingFinalizers();
        }
    }
}
```

### 错误处理策略

#### 1. 分层错误处理

```csharp
public class CadOperationService
{
    // 业务层：处理业务逻辑错误
    public Result<List<Entity>> GetEntitiesInRegion(Rect region)
    {
        try
        {
            return ExecuteWithErrorHandling(() =>
            {
                using (var tr = new DBTrans())
                {
                    var entities = tr.CurrentSpace.GetEntities<Entity>();
                    var quadTree = new QuadTree<Entity>(region);

                    foreach (var entity in entities)
                    {
                        quadTree.Insert(entity);
                    }

                    var result = quadTree.Query(region, QuadTreeSelectMode.IntersectsWith);
                    tr.Commit();

                    return Result<List<Entity>>.Success(result);
                }
            });
        }
        catch (Exception ex)
        {
            return Result<List<Entity>>.Failure($"获取区域实体失败: {ex.Message}");
        }
    }

    // 基础设施层：处理技术错误
    private T ExecuteWithErrorHandling<T>(Func<T> operation)
    {
        try
        {
            return operation();
        }
        catch (AcException acEx)
        {
            ErrorInfoEx.AcErrorInfo(acEx);
            throw new CadOperationException("CAD操作失败", acEx);
        }
        catch (GetPeMethodException peEx)
        {
            LogPeError(peEx);
            throw new CadOperationException("PE方法调用失败", peEx);
        }
    }

    private void LogPeError(GetPeMethodException peEx)
    {
        var errorType = (GetMethodErrorNum)peEx.ErrorNum;
        switch (errorType)
        {
            case GetMethodErrorNum.NoModule:
                Console.WriteLine("模块未找到");
                break;
            case GetMethodErrorNum.NoFuncName:
                Console.WriteLine("函数未找到");
                break;
        }
    }
}

// 结果包装类
public class Result<T>
{
    public bool IsSuccess { get; private set; }
    public T Data { get; private set; }
    public string ErrorMessage { get; private set; }

    public static Result<T> Success(T data) => new Result<T> { IsSuccess = true, Data = data };
    public static Result<T> Failure(string error) => new Result<T> { IsSuccess = false, ErrorMessage = error };
}
```

#### 2. 统一异常处理

```csharp
public class CadOperationException : Exception
{
    public CadOperationException(string message) : base(message) { }
    public CadOperationException(string message, Exception innerException) : base(message, innerException) { }
}

// 全局异常处理器
public static class GlobalExceptionHandler
{
    public static void HandleException(Exception ex, string context = "")
    {
        var message = $"[{context}] {ex.Message}";

        switch (ex)
        {
            case AcException acEx:
                ErrorInfoEx.AcErrorInfo(acEx);
                break;

            case GetPeMethodException peEx:
                EditorEx.WriteMessage($"PE错误 [{peEx.ErrorNum}]: {peEx.ErrorMsg}");
                break;

            case CadOperationException cadEx:
                EditorEx.WriteMessage($"CAD操作错误: {cadEx.Message}");
                break;

            default:
                EditorEx.WriteMessage($"未知错误: {message}");
                break;
        }

        // 记录到日志文件
        LogToFile(ex, context);
    }

    private static void LogToFile(Exception ex, string context)
    {
        var logPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.ApplicationData),
                                  "IFoxCAD", "Logs", $"error_{DateTime.Now:yyyyMMdd}.log");

        Directory.CreateDirectory(Path.GetDirectoryName(logPath));

        var logEntry = $"[{DateTime.Now:yyyy-MM-dd HH:mm:ss}] [{context}] {ex}\n";
        File.AppendAllText(logPath, logEntry);
    }
}
```

### 代码组织

#### 1. 命令类组织

```csharp
// 按功能模块组织命令
[CommandClass]
public class EntityCommands
{
    [CommandMethod("CREATELINE")]
    public void CreateLine()
    {
        try
        {
            var service = new EntityCreationService();
            service.CreateLine();
        }
        catch (Exception ex)
        {
            GlobalExceptionHandler.HandleException(ex, "CreateLine");
        }
    }

    [CommandMethod("MOVELINE")]
    public void MoveLine()
    {
        try
        {
            var service = new EntityModificationService();
            service.MoveSelectedEntities();
        }
        catch (Exception ex)
        {
            GlobalExceptionHandler.HandleException(ex, "MoveLine");
        }
    }
}

[CommandClass]
public class QueryCommands
{
    [CommandMethod("QUERYREGION")]
    public void QueryRegion()
    {
        try
        {
            var service = new SpatialQueryService();
            service.QueryEntitiesInRegion();
        }
        catch (Exception ex)
        {
            GlobalExceptionHandler.HandleException(ex, "QueryRegion");
        }
    }
}
```

#### 2. 服务层设计

```csharp
// 实体创建服务
public class EntityCreationService
{
    private readonly IUserInputService _inputService;
    private readonly IEntityRepository _entityRepository;

    public EntityCreationService()
    {
        _inputService = new UserInputService();
        _entityRepository = new EntityRepository();
    }

    public void CreateLine()
    {
        var startPoint = _inputService.GetPoint("指定起点:");
        if (!startPoint.HasValue) return;

        var endPoint = _inputService.GetPoint("指定终点:", startPoint.Value);
        if (!endPoint.HasValue) return;

        var line = new Line(startPoint.Value, endPoint.Value);
        _entityRepository.Add(line);

        EditorEx.WriteMessage($"直线创建完成，长度: {line.Length:F2}");
    }
}

// 用户输入服务
public interface IUserInputService
{
    Point3d? GetPoint(string prompt, Point3d? basePoint = null);
    double? GetDistance(string prompt, double defaultValue = 1.0);
    string GetString(string prompt, string defaultValue = "");
}

public class UserInputService : IUserInputService
{
    private readonly Editor _editor;

    public UserInputService()
    {
        _editor = Application.DocumentManager.MdiActiveDocument.Editor;
    }

    public Point3d? GetPoint(string prompt, Point3d? basePoint = null)
    {
        var options = new PromptPointOptions(prompt);
        if (basePoint.HasValue)
        {
            options.BasePoint = basePoint.Value;
            options.UseBasePoint = true;
        }

        var result = _editor.GetPoint(options);
        return result.Status == PromptStatus.OK ? result.Value : (Point3d?)null;
    }

    public double? GetDistance(string prompt, double defaultValue = 1.0)
    {
        var result = EditorEx.GetDouble(_editor, prompt, defaultValue);
        return result.Status == PromptStatus.OK ? result.Value : (double?)null;
    }

    public string GetString(string prompt, string defaultValue = "")
    {
        var result = EditorEx.GetString(_editor, prompt, defaultValue);
        return result.Status == PromptStatus.OK ? result.StringResult : null;
    }
}

// 实体仓储
public interface IEntityRepository
{
    void Add(Entity entity);
    void Update(Entity entity);
    void Remove(ObjectId entityId);
    T GetById<T>(ObjectId id) where T : Entity;
    IEnumerable<T> GetAll<T>() where T : Entity;
}

public class EntityRepository : IEntityRepository
{
    public void Add(Entity entity)
    {
        using (var tr = new DBTrans())
        {
            tr.CurrentSpace.AddEntity(entity);
            tr.Commit();
        }
    }

    public void Update(Entity entity)
    {
        using (var tr = new DBTrans())
        {
            var dbEntity = tr.GetObject<Entity>(entity.ObjectId, OpenMode.ForWrite);
            // 更新属性
            tr.Commit();
        }
    }

    public void Remove(ObjectId entityId)
    {
        using (var tr = new DBTrans())
        {
            var entity = tr.GetObject<Entity>(entityId, OpenMode.ForWrite);
            entity.Erase();
            tr.Commit();
        }
    }

    public T GetById<T>(ObjectId id) where T : Entity
    {
        using (var tr = new DBTrans())
        {
            return tr.GetObject<T>(id);
        }
    }

    public IEnumerable<T> GetAll<T>() where T : Entity
    {
        using (var tr = new DBTrans())
        {
            return tr.CurrentSpace.GetEntities<T>();
        }
    }
}
```

### 内存管理

#### 1. 大数据处理

```csharp
// 分批处理大量数据
public class LargeDataProcessor
{
    private const int BATCH_SIZE = 1000;

    public void ProcessLargeEntitySet(IEnumerable<ObjectId> entityIds)
    {
        var batches = entityIds.Batch(BATCH_SIZE);
        var processedCount = 0;

        foreach (var batch in batches)
        {
            ProcessBatch(batch);
            processedCount += batch.Count();

            // 定期报告进度
            if (processedCount % (BATCH_SIZE * 10) == 0)
            {
                EditorEx.WriteMessage($"已处理 {processedCount} 个实体...");

                // 强制垃圾回收（谨慎使用）
                GC.Collect();
                GC.WaitForPendingFinalizers();
            }
        }

        EditorEx.WriteMessage($"处理完成，总计 {processedCount} 个实体。");
    }

    private void ProcessBatch(IEnumerable<ObjectId> batch)
    {
        using (var tr = new DBTrans())
        {
            foreach (var id in batch)
            {
                try
                {
                    var entity = tr.GetObject<Entity>(id, OpenMode.ForWrite);
                    // 处理实体
                    ProcessEntity(entity);
                }
                catch (Exception ex)
                {
                    // 记录错误但继续处理其他实体
                    Console.WriteLine($"处理实体 {id} 时出错: {ex.Message}");
                }
            }
            tr.Commit();
        }
    }

    private void ProcessEntity(Entity entity)
    {
        // 具体的实体处理逻辑
        switch (entity)
        {
            case Line line:
                ProcessLine(line);
                break;
            case Circle circle:
                ProcessCircle(circle);
                break;
            // 其他实体类型...
        }
    }
}

// LINQ扩展：分批处理
public static class EnumerableExtensions
{
    public static IEnumerable<IEnumerable<T>> Batch<T>(this IEnumerable<T> source, int batchSize)
    {
        var batch = new List<T>(batchSize);
        foreach (var item in source)
        {
            batch.Add(item);
            if (batch.Count == batchSize)
            {
                yield return batch;
                batch = new List<T>(batchSize);
            }
        }

        if (batch.Count > 0)
        {
            yield return batch;
        }
    }
}
```

#### 2. 资源监控

```csharp
// 内存使用监控
public class MemoryMonitor
{
    private static readonly Timer _timer;
    private static long _lastMemoryUsage;

    static MemoryMonitor()
    {
        _timer = new Timer(CheckMemoryUsage, null, TimeSpan.FromMinutes(1), TimeSpan.FromMinutes(1));
    }

    private static void CheckMemoryUsage(object state)
    {
        var currentMemory = GC.GetTotalMemory(false);
        var memoryInMB = currentMemory / 1024 / 1024;

        if (memoryInMB > 500) // 超过500MB时警告
        {
            Console.WriteLine($"内存使用警告: {memoryInMB} MB");

            if (memoryInMB > 1000) // 超过1GB时强制回收
            {
                GC.Collect();
                GC.WaitForPendingFinalizers();
                GC.Collect();

                var afterGC = GC.GetTotalMemory(false) / 1024 / 1024;
                Console.WriteLine($"垃圾回收后内存: {afterGC} MB");
            }
        }

        _lastMemoryUsage = currentMemory;
    }

    public static void LogMemoryUsage(string context)
    {
        var memory = GC.GetTotalMemory(false) / 1024 / 1024;
        Console.WriteLine($"[{context}] 内存使用: {memory} MB");
    }
}
```

## 关键词索引

### A-C
- **API封装** → [PInvokeUser32](#pinvokeuser32-系统api封装类), [WindowsAPI](#windowsapi-系统工具类)
- **AutoCAD** → [EditorEx](#编辑器扩展-editorex), [EntityEx](#实体操作-entityex)
- **Array数组** → [ArrayEx](#arrayex-数组扩展类)
- **Association关联** → [AssocPersSubentityIdPEEx](#关联子实体扩展-assocperssubentityidpeex), [AssocUtils](#关联动作工具-assocutils)
- **Batch批处理** → [最佳实践](#最佳实践)
- **Circle圆** → [CircleEx](#实体操作-entityex)
- **Configuration配置** → [QuadTreeEvn](#quadtreeevn-四叉树环境变量)
- **Coordinate坐标** → [CoordinateSystemCode](#coordinatesystemcode-坐标系类型)

### D-H
- **Database数据库** → [DatabaseEx](#数据库扩展-databaseex), [DBTrans](#事务管理-dbtrans)
- **Debug调试** → [DebugEx](#debugex-调试工具类)
- **Document文档** → [DocumentLockManager](#文档锁管理器-documentlockmanager)
- **DWG文件** → [DwgMark](#dwg文件标记管理-dwgmark)
- **Editor编辑器** → [EditorEx](#编辑器扩展-editorex)
- **Entity实体** → [EntityEx](#实体操作-entityex)
- **Enum枚举** → [EnumEx](#enumex-枚举扩展类)
- **Error错误** → [ErrorInfoEx](#cad错误信息处理-errorinfoex), [GetPeMethodException](#pe方法专用异常类)
- **Exception异常** → [GetPeMethodException](#pe方法专用异常类)
- **Font字体** → [FontTTF](#fontttf-字体类型枚举)
- **Hatch填充** → [HatchEx](#填充扩展-hatchex)

### I-P
- **Index索引** → [QuadTree](#四叉树-quadtree)
- **Input输入** → [EditorEx](#编辑器扩展-editorex)
- **Jig夹点** → [JigEx](#夹点操作-jigex)
- **LINQ** → [LinqEx](#linqex-linq扩展类)
- **Line直线** → [EntityEx](#实体操作-entityex)
- **List列表** → [LoopList](#looplist-环链表类)
- **Lock锁定** → [DocumentLockManager](#文档锁管理器-documentlockmanager)
- **Loop循环** → [LoopList](#looplist-环链表类)
- **Memory内存** → [最佳实践](#最佳实践)
- **PE文件** → [PeInfo](#pe文件信息分析系统), [AcadPeInfo](#pe文件信息分析系统)
- **Performance性能** → [最佳实践](#最佳实践), [QuadTree](#四叉树-quadtree)
- **Point点** → [EditorEx](#编辑器扩展-editorex)
- **Polyline多段线** → [PolylineEx](#实体操作-entityex)

### Q-Z
- **QuadTree四叉树** → [QuadTree](#四叉树-quadtree), [QuadTreeEvn](#quadtreeevn-四叉树环境变量)
- **Query查询** → [QuadTree](#四叉树-quadtree)
- **Random随机** → [RandomEx](#randomex-随机数扩展类)
- **Selection选择** → [SelectionSetEx](#选择集扩展-selectionsetex)
- **Spatial空间** → [QuadTree](#四叉树-quadtree)
- **System系统** → [SystemEx](#systemex-系统扩展类)
- **Transaction事务** → [DBTrans](#事务管理-dbtrans)
- **UI界面** → [PaneMarginType](#panemargintype-托盘边距类型)
- **User用户** → [EditorEx](#编辑器扩展-editorex)
- **Validation验证** → [ArgumentNullEx](#argumentnullex-参数验证类)
- **Windows** → [PInvokeUser32](#pinvokeuser32-系统api封装类), [WindowsAPI](#windowsapi-系统工具类)
- **Xref外部参照** → [XrefModes](#xrefmodes-外部参照模式)

## 方法索引

### 常用方法快速查找

#### 实体操作方法
- **创建实体** → `tr.CurrentSpace.AddEntity()` - [DBTrans](#事务管理-dbtrans)
- **移动实体** → `EntityEx.Move()` - [EntityEx](#实体操作-entityex)
- **旋转实体** → `EntityEx.Rotate()` - [EntityEx](#实体操作-entityex)
- **缩放实体** → `EntityEx.Scale()` - [EntityEx](#实体操作-entityex)
- **镜像实体** → `EntityEx.Mirror()` - [EntityEx](#实体操作-entityex)
- **复制实体** → `EntityEx.Copy()` - [EntityEx](#实体操作-entityex)

#### 用户交互方法
- **获取点** → `EditorEx.GetPoint()` - [EditorEx](#编辑器扩展-editorex)
- **获取距离** → `EditorEx.GetDistance()` - [EditorEx](#编辑器扩展-editorex)
- **获取角度** → `EditorEx.GetAngle()` - [EditorEx](#编辑器扩展-editorex)
- **获取字符串** → `EditorEx.GetString()` - [EditorEx](#编辑器扩展-editorex)
- **选择实体** → `EditorEx.GetSelection()` - [EditorEx](#编辑器扩展-editorex)
- **写入消息** → `EditorEx.WriteMessage()` - [EditorEx](#编辑器扩展-editorex)

#### 空间查询方法
- **插入对象** → `QuadTree.Insert()` - [QuadTree](#四叉树-quadtree)
- **查询区域** → `QuadTree.Query()` - [QuadTree](#四叉树-quadtree)
- **查找邻居** → `QuadTree.FindNeibor()` - [QuadTree](#四叉树-quadtree)
- **移除对象** → `QuadTree.Remove()` - [QuadTree](#四叉树-quadtree)
- **清空树** → `QuadTree.Clear()` - [QuadTree](#四叉树-quadtree)

#### 数据库操作方法
- **开始事务** → `new DBTrans()` - [DBTrans](#事务管理-dbtrans)
- **提交事务** → `tr.Commit()` - [DBTrans](#事务管理-dbtrans)
- **获取对象** → `tr.GetObject<T>()` - [DBTrans](#事务管理-dbtrans)
- **获取实体** → `tr.CurrentSpace.GetEntities<T>()` - [DBTrans](#事务管理-dbtrans)
- **切换数据库** → `new SwitchDatabase()` - [数据库切换](#数据库切换-switchdatabase)

#### 填充操作方法
- **创建填充** → `HatchEx.CreateHatch()` - [HatchEx](#填充扩展-hatchex)
- **设置边界** → `HatchEx.SetBoundary()` - [HatchEx](#填充扩展-hatchex)
- **获取边界** → `HatchEx.GetAssociatedBoundaryIds()` - [HatchEx](#填充扩展-hatchex)
- **重置边界** → `HatchEx.ResetBoundarys()` - [HatchEx](#填充扩展-hatchex)

#### 工具类方法
- **数组合并** → `ArrayEx.Combine2()` - [ArrayEx](#arrayex-数组扩展类)
- **数组去重** → `ArrayEx.Deduplication()` - [ArrayEx](#arrayex-数组扩展类)
- **查找最大值** → `LinqEx.FindByMax()` - [LinqEx](#linqex-linq扩展类)
- **查找最小值** → `LinqEx.FindByMin()` - [LinqEx](#linqex-linq扩展类)
- **环链表添加** → `LoopList.Add()` - [LoopList](#looplist-环链表类)
- **环链表遍历** → `LoopList.ForEach()` - [LoopList](#looplist-环链表类)

### 按功能分类的方法索引

#### 🏗️ 基础设施方法
```
DBTrans:
├── 构造函数: new DBTrans(), new DBTrans(Database)
├── 事务管理: Commit(), Abort(), Dispose()
├── 对象获取: GetObject<T>(), GetObjects<T>()
├── 实体操作: CurrentSpace.AddEntity(), CurrentSpace.GetEntities<T>()
└── 表访问: BlockTable, LayerTable, TextStyleTable

DocumentLockManager:
├── 锁定管理: LockDocument(), UnlockDocument()
├── 状态检查: IsLocked(), GetLockStatus()
└── 批量操作: ExecuteInLock()
```

#### 📐 实体操作方法
```
EntityEx:
├── 变换操作: Move(), Rotate(), Scale(), Mirror()
├── 复制操作: Copy(), CopyTo()
├── 属性设置: SetLayer(), SetColor(), SetLinetype()
└── 几何计算: GetBounds(), GetCenter()

HatchEx:
├── 创建填充: CreateHatch(), CreateBoundaryHatch()
├── 边界管理: SetBoundary(), GetAssociatedBoundaryIds()
├── 样式设置: SetPattern(), SetScale()
└── 关联性: ResetBoundarys(), UpdateAssociativity()
```

#### 🖱️ 用户交互方法
```
EditorEx:
├── 点输入: GetPoint(), GetCorner(), GetDistance()
├── 选择操作: GetSelection(), GetEntity(), GetKeywords()
├── 输入获取: GetString(), GetInteger(), GetDouble()
├── 视图控制: ZoomExtents(), ZoomWindow(), ZoomPrevious()
└── 消息输出: WriteMessage(), UpdateScreen()

JigEx:
├── 夹点创建: CreateJig(), StartJig()
├── 动态预览: UpdatePreview(), GetDynamicDimension()
└── 用户交互: GetPoint(), GetAngle(), GetDistance()
```

#### 🔍 空间查询方法
```
QuadTree<T>:
├── 构建操作: Insert(), InsertRange()
├── 查询操作: Query(), QueryRange(), FindNeibor()
├── 维护操作: Remove(), Clear(), Rebuild()
└── 统计信息: Count(), GetDepth(), GetBounds()
```

#### 🛠️ 工具类方法
```
ArrayEx:
├── 合并操作: Combine2(), CombineMultiple()
├── 去重操作: Deduplication(), DeduplicationBy()
└── 转换操作: ToArray(), ToList()

LinqEx:
├── 查找操作: FindByMax(), FindByMin(), FindByCondition()
├── 排序操作: SortBy(), OrderByMultiple()
└── 分组操作: GroupByKey(), PartitionBy()

LoopList<T>:
├── 添加操作: Add(), Insert(), AddRange()
├── 删除操作: Remove(), RemoveAt(), Clear()
├── 查找操作: Find(), FindAll(), Contains()
├── 遍历操作: ForEach(), ForEachReverse()
└── 转换操作: ToArray(), ToList(), Reverse()
```

## 交叉引用表

### 类与枚举的关系
| 类名 | 相关枚举 | 用途 |
|------|----------|------|
| QuadTree | QuadTreeSelectMode, QuadTreeFindMode | 查询模式控制 |
| EditorEx | RunLispFlag, SingleKeyWordWorkType | Lisp执行和交互模式 |
| DatabaseEx | SymModes, XrefModes | 符号表和外部参照操作 |
| PeInfo | AcadPeEnum, GetMethodErrorNum | PE文件分析和错误处理 |
| DBmodEx | DBmod | 数据库修改状态管理 |

### 配置与类的关系
| 配置类 | 影响的功能类 | 配置项 |
|--------|--------------|--------|
| QuadTreeEvn | QuadTree | MinArea, MaxDepth, SplitCount |

### 异常与处理类的关系
| 异常类 | 处理类 | 相关枚举 |
|--------|--------|----------|
| GetPeMethodException | ErrorInfoEx | GetMethodErrorNum |
| AcException | ErrorInfoEx | - |

---

*本文档基于 IFoxCAD.AutoCAD 0.9.6 版本编写，专为 Context7 AI 上下文平台优化，帮助 AI 助手更好地理解和使用该库协助开发者进行 AutoCAD 开发任务。*
