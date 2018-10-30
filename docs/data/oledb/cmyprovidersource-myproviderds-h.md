---
title: CCustomSource (CustomDS.H) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- myproviderds.h
- cmyprovidersource
- customds.h
- ccustomsource
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderSource class in MyProviderDS.H
- CCustomSource class in CustomDS.H
ms.assetid: c143d48e-59c8-4f67-9141-3aab51859b92
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3ad9a2c9ac2d7371cc1fb357e2ce6a9e35701607
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216386"
---
# <a name="ccustomsource-customdsh"></a>CCustomSource (CustomDS.h)

Klasy dostawców używają wielokrotnego dziedziczenia. Poniższy kod pokazuje łańcuch dziedziczenia dla obiektu źródła danych:

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSource
class ATL_NO_VTABLE CCustomSource :
   public CComObjectRootEx<CComSingleThreadModel>,
   public CComCoClass<CCustomSource, &CLSID_Custom>,
   public IDBCreateSessionImpl<CCustomSource, CCustomSession>,
   public IDBInitializeImpl<CCustomSource>,
   public IDBPropertiesImpl<CCustomSource>,
   public IPersistImpl<CCustomSource>,
   public IInternalConnectionImpl<CCustomSource>
```

Wszystkie składniki modelu COM pochodzi od `CComObjectRootEx` i `CComCoClass`. `CComObjectRootEx` zawiera wszystkie wdrożenia dla `IUnknown` interfejsu. Może obsługiwać żadnych modelu wątkowości. `CComCoClass` obsługuje każdy rodzaj pomocy technicznej błąd wymagane. Jeśli chcesz wysłać bogatsze informacje o błędzie do klienta, możesz użyć niektórych błędów interfejsów API w `CComCoClass`.

Obiekt źródła danych dziedziczy także kilka klas "Impl". Każda klasa zawiera implementację interfejsu. Źródła danych, obiekt implementuje `IPersist`, `IDBProperties`, `IDBInitialize`, i `IDBCreateSession` interfejsów. Każdy interfejs jest wymagany przez OLE DB implementacji obiektu źródła danych. Istnieje możliwość obsługi lub nie obsługuje określonej funkcji poprzez dziedziczenie lub nie dziedziczy z jednej z tych klas "Impl". Jeśli chcesz obsługiwać `IDBDataSourceAdmin` interfejsu, dziedziczą z `IDBDataSourceAdminImpl` klasy, aby uzyskać funkcje wymagane.

## <a name="com-map"></a>Mapy interfejsu COM

Zawsze, gdy klient wywołuje `QueryInterface` interfejsu w źródle danych, przechodzi on przez następujące mapy interfejsu COM:

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSource
class ATL_NO_VTABLE CCustomSource : 
   public CComObjectRootEx<CComSingleThreadModel>,
   public CComCoClass<CCustomSource, &CLSID_Custom>,
   public IDBCreateSessionImpl<CCustomSource, CCustomSession>,
   public IDBInitializeImpl<CCustomSource>,
   public IDBPropertiesImpl<CCustomSource>,
   public IPersistImpl<CCustomSource>,
   public IInternalConnectionImpl<CCustomSource>
```

Wszystkie składniki modelu COM pochodzi od `CComObjectRootEx` i `CComCoClass`. `CComObjectRootEx` zawiera wszystkie wdrożenia dla `IUnknown` interfejsu. Może obsługiwać żadnych modelu wątkowości. `CComCoClass` obsługuje każdy rodzaj pomocy technicznej błąd wymagane. Jeśli chcesz wysłać bogatsze informacje o błędzie do klienta, możesz użyć niektórych błędów interfejsów API w `CComCoClass`.

Obiekt źródła danych dziedziczy także kilka klas "Impl". Każda klasa zawiera implementację interfejsu. Źródła danych, obiekt implementuje `IPersist`, `IDBProperties`, `IDBInitialize`, i `IDBCreateSession` interfejsów. Każdy interfejs jest wymagany przez OLE DB implementacji obiektu źródła danych. Istnieje możliwość obsługi lub nie obsługuje określonej funkcji poprzez dziedziczenie lub nie dziedziczy z jednej z tych klas "Impl". Jeśli chcesz obsługiwać `IDBDataSourceAdmin` interfejsu, dziedziczą z `IDBDataSourceAdminImpl` klasy, aby uzyskać funkcje wymagane.

## <a name="com-map"></a>Mapy interfejsu COM

Zawsze, gdy klient wywołuje `QueryInterface` interfejsu w źródle danych, przechodzi on przez następujące mapy interfejsu COM:

```cpp
BEGIN_COM_MAP(CCustomSource)
   COM_INTERFACE_ENTRY(IDBCreateSession)
   COM_INTERFACE_ENTRY(IDBInitialize)
   COM_INTERFACE_ENTRY(IDBProperties)
   COM_INTERFACE_ENTRY(IPersist)
   COM_INTERFACE_ENTRY(IInternalConnection)
END_COM_MAP()
```

Makra com_interface_entry — z ATL i wykonania `QueryInterface` w `CComObjectRootEx` do zwrócenia odpowiednich interfejsów.

## <a name="property-map"></a>Mapy właściwości

Mapy właściwości określa wszystkie właściwości, które są przypisane przez dostawcę:

```cpp
BEGIN_PROPSET_MAP(CCustomSource)
   BEGIN_PROPERTY_SET(DBPROPSET_DATASOURCEINFO)
      PROPERTY_INFO_ENTRY(ACTIVESESSIONS)
      PROPERTY_INFO_ENTRY(ASYNCTXNABORT)
      PROPERTY_INFO_ENTRY(ASYNCTXNCOMMIT)
      PROPERTY_INFO_ENTRY(BYREFACCESSORS)
      PROPERTY_INFO_ENTRY_VALUE(CATALOGLOCATION, DBPROPVAL_CL_START)
      PROPERTY_INFO_ENTRY(CATALOGTERM)
      PROPERTY_INFO_ENTRY(CATALOGUSAGE)
      PROPERTY_INFO_ENTRY(COLUMNDEFINITION)
      PROPERTY_INFO_ENTRY(CONCATNULLBEHAVIOR)
      PROPERTY_INFO_ENTRY(DATASOURCENAME)
      PROPERTY_INFO_ENTRY(DATASOURCEREADONLY)
      PROPERTY_INFO_ENTRY(DBMSNAME)
      PROPERTY_INFO_ENTRY(DBMSVER)
      PROPERTY_INFO_ENTRY_VALUE(DSOTHREADMODEL, DBPROPVAL_RT_FREETHREAD)
      PROPERTY_INFO_ENTRY(GROUPBY)
      PROPERTY_INFO_ENTRY(HETEROGENEOUSTABLES)
      PROPERTY_INFO_ENTRY(IDENTIFIERCASE)
      PROPERTY_INFO_ENTRY(MAXINDEXSIZE)
      PROPERTY_INFO_ENTRY(MAXROWSIZE)
      PROPERTY_INFO_ENTRY(MAXROWSIZEINCLUDESBLOB)
      PROPERTY_INFO_ENTRY(MAXTABLESINSELECT)
      PROPERTY_INFO_ENTRY(MULTIPLEPARAMSETS)
      PROPERTY_INFO_ENTRY(MULTIPLERESULTS)
      PROPERTY_INFO_ENTRY(MULTIPLESTORAGEOBJECTS)
      PROPERTY_INFO_ENTRY(MULTITABLEUPDATE)
      PROPERTY_INFO_ENTRY(NULLCOLLATION)
      PROPERTY_INFO_ENTRY(OLEOBJECTS)
      PROPERTY_INFO_ENTRY(ORDERBYCOLUMNSINSELECT)
      PROPERTY_INFO_ENTRY(OUTPUTPARAMETERAVAILABILITY)
      PROPERTY_INFO_ENTRY(PERSISTENTIDTYPE)
      PROPERTY_INFO_ENTRY(PREPAREABORTBEHAVIOR)
      PROPERTY_INFO_ENTRY(PREPARECOMMITBEHAVIOR)
      PROPERTY_INFO_ENTRY(PROCEDURETERM)
      PROPERTY_INFO_ENTRY(PROVIDERNAME)
      PROPERTY_INFO_ENTRY(PROVIDEROLEDBVER)
      PROPERTY_INFO_ENTRY(PROVIDERVER)
      PROPERTY_INFO_ENTRY(QUOTEDIDENTIFIERCASE)
      PROPERTY_INFO_ENTRY(ROWSETCONVERSIONSONCOMMAND)
      PROPERTY_INFO_ENTRY(SCHEMATERM)
      PROPERTY_INFO_ENTRY(SCHEMAUSAGE)
      PROPERTY_INFO_ENTRY(STRUCTUREDSTORAGE)
      PROPERTY_INFO_ENTRY(SUBQUERIES)
      PROPERTY_INFO_ENTRY(TABLETERM)
      PROPERTY_INFO_ENTRY(USERNAME)
   END_PROPERTY_SET(DBPROPSET_DATASOURCEINFO)
   BEGIN_PROPERTY_SET(DBPROPSET_DBINIT)
      PROPERTY_INFO_ENTRY(AUTH_PASSWORD)
      PROPERTY_INFO_ENTRY(AUTH_PERSIST_SENSITIVE_AUTHINFO)
      PROPERTY_INFO_ENTRY(AUTH_USERID)
      PROPERTY_INFO_ENTRY(INIT_DATASOURCE)
      PROPERTY_INFO_ENTRY(INIT_HWND)
      PROPERTY_INFO_ENTRY(INIT_LCID)
      PROPERTY_INFO_ENTRY(INIT_LOCATION)
      PROPERTY_INFO_ENTRY(INIT_MODE)
      PROPERTY_INFO_ENTRY(INIT_PROMPT)
      PROPERTY_INFO_ENTRY(INIT_PROVIDERSTRING)
      PROPERTY_INFO_ENTRY(INIT_TIMEOUT)
   END_PROPERTY_SET(DBPROPSET_DBINIT)
   BEGIN_PROPERTY_SET(DBPROPSET_DATASOURCE)
      PROPERTY_INFO_ENTRY(CURRENTCATALOG)
   END_PROPERTY_SET(DBPROPSET_DATASOURCE)
   CHAIN_PROPERTY_SET(CCustomSession)
END_PROPSET_MAP()
```

Właściwości w OLE DB są zgrupowane. Obiekt źródła danych ma dwie grupy właściwości: jeden dla DBPROPSET_DATASOURCEINFO zestawu i jeden dla DBPROPSET_DBINIT, które zostały zestawu. Zestaw DBPROPSET_DATASOURCEINFO odnosi się do właściwości o dostawcy i źródła danych. Zestaw DBPROPSET_DBINIT odnosi się do właściwości używanych podczas inicjowania. Szablony OLE DB Provider obsługiwać te zestawy z makrami PROPERTY_SET. Makra Tworzenie bloku, który zawiera szereg właściwości. Zawsze, gdy klient wywołuje `IDBProperties` interfejsu dostawcę używa mapy właściwości.

Nie trzeba zaimplementować dla każdej właściwości w specyfikacji. Jednak musi obsługiwać wymagane właściwości; zobacz specyfikację zgodności poziomu 0, aby uzyskać więcej informacji. Jeśli nie chcesz obsługiwać właściwości, możesz go usunąć z mapy. Jeśli chcesz obsługiwać właściwość, dodać go do mapy, przy użyciu PROPERTY_INFO_ENTRY — makro. Makro odnosi się do `UPROPINFO` struktury, jak pokazano w poniższym kodzie:

```cpp
struct UPROPINFO
{
   DBPROPID    dwPropId;
   ULONG       ulIDS;
   VARTYPE     VarType;
   DBPROPFLAGS dwFlags;
   union
   {
      DWORD dwVal;
      LPOLESTR szVal;
   };
   DBPROPOPTIONS dwOption;
};
```

Każdy element w strukturze reprezentuje informacje w celu obsługi właściwości. Zawiera on `DBPROPID` Aby określić identyfikator GUID i identyfikator właściwości. Zawiera ona także wpisy, aby określić typ i wartość właściwości.

Jeśli chcesz zmienić wartość domyślną właściwości (Uwaga konsument może zmienić wartość właściwości z możliwością zapisu w dowolnym momencie), można użyć makra PROPERTY_INFO_ENTRY_VALUE albo PROPERTY_INFO_ENTRY_EX. Te makra umożliwiają określenie wartości dla odpowiednich właściwości. PROPERTY_INFO_ENTRY_VALUE — makro jest skróconą notacją, która pozwala na zmianę wartości. PROPERTY_INFO_ENTRY_VALUE — makro wywołuje PROPERTY_INFO_ENTRY_EX — makro. Umożliwia to makro, możesz dodać lub zmienić wszystkie atrybuty w `UPROPINFO` struktury.

Jeśli chcesz zdefiniować własny zestaw właściwości, można dodać jeden, wprowadzając dodatkowe kombinacji BEGIN_PROPSET_MAP/END_PROPSET_MAP. Zdefiniuj identyfikator GUID dla zestawu właściwości, a następnie zdefiniować własne właściwości. W przypadku właściwości specyficzne dla dostawcy, należy je dodać nową właściwość, ustaw zamiast przy użyciu istniejącego. Umożliwia to uniknięcie problemów w nowszych wersjach OLE DB.

## <a name="user-defined-property-sets"></a>Zestawy właściwości zdefiniowanych przez użytkownika

Visual C++ obsługuje zestawów zdefiniowanych przez użytkownika właściwości. Nie trzeba zastąpić `GetProperties` lub `GetPropertyInfo`. Zamiast tego szablony wykryć każdy zestaw zdefiniowanych przez użytkownika właściwości i dodać go do odpowiedniego obiektu.

Jeśli masz zestaw właściwości zdefiniowanych przez użytkownika, które muszą być dostępne w czasie inicjowania (oznacza to, zanim użytkownik wywołuje `IDBInitialize::Initialize`), należy to określić za pomocą flagi UPROPSET_USERINIT wraz z BEGIN_PROPERTY_SET_EX — makro. Musi mieć ustawioną właściwość obiektu źródła danych, w tym pracę (wymaga specyfikacji OLE DB). Na przykład:

```cpp
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)
```

## <a name="see-also"></a>Zobacz też

[Pliki dostawcy generowane przez kreatora](../../data/oledb/provider-wizard-generated-files.md)<br/>
