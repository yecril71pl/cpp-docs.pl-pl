---
title: CCustomSource (CustomDS.H)
ms.date: 10/22/2018
f1_keywords:
- myproviderds.h
- cmyprovidersource
- customds.h
- ccustomsource
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderSource class in MyProviderDS.H
- CCustomSource class in CustomDS.H
ms.assetid: c143d48e-59c8-4f67-9141-3aab51859b92
ms.openlocfilehash: 8e92c30e8d62ade095167880917ad70da8e59b36
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742921"
---
# <a name="ccustomsource-customdsh"></a>CCustomSource (CustomDS. h)

Klasy dostawców używają wielu dziedziczeń. Poniższy kod przedstawia łańcuch dziedziczenia dla obiektu źródła danych:

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

Wszystkie składniki modelu COM pochodzą z `CComObjectRootEx` i `CComCoClass` . `CComObjectRootEx` zawiera wszystkie implementacje `IUnknown` interfejsu. Może obsługiwać dowolny model wątkowości. `CComCoClass` obsługuje wszystkie wymagane wymagania dotyczące obsługi błędów. Jeśli chcesz wysłać bogatsze informacje o błędzie do klienta, możesz użyć niektórych interfejsów API błędów w `CComCoClass` .

Obiekt źródła danych dziedziczy również z kilku klas "Impl". Każda Klasa zawiera implementację interfejsu. Obiekt źródła danych implementuje `IPersist` `IDBProperties` interfejsy,, `IDBInitialize` , i `IDBCreateSession` . Każdy interfejs jest wymagany przez OLE DB w celu zaimplementowania obiektu źródła danych. Można wybrać opcję obsługi lub nieobsługi określonych funkcji przez dziedziczenie lub niedziedziczenie z jednej z tych klas "Impl". Jeśli chcesz obsługiwać `IDBDataSourceAdmin` interfejs, dziedziczysz z `IDBDataSourceAdminImpl` klasy w celu uzyskania wymaganych funkcji.

## <a name="com-map"></a>Mapa COM

Za każdym razem, gdy klient wywołuje `QueryInterface` interfejs w źródle danych, przechodzi przez następującą mapę com:

```cpp
BEGIN_COM_MAP(CCustomSource)
   COM_INTERFACE_ENTRY(IDBCreateSession)
   COM_INTERFACE_ENTRY(IDBInitialize)
   COM_INTERFACE_ENTRY(IDBProperties)
   COM_INTERFACE_ENTRY(IPersist)
   COM_INTERFACE_ENTRY(IInternalConnection)
END_COM_MAP()
```

Makra COM_INTERFACE_ENTRY pochodzą z ATL i informują o implementacji programu `QueryInterface` w `CComObjectRootEx` celu zwrócenia odpowiednich interfejsów.

## <a name="property-map"></a>Mapa właściwości

Mapa właściwości określa wszystkie właściwości przypisane przez dostawcę:

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

Właściwości w OLE DB są zgrupowane. Obiekt źródła danych ma dwie grupy właściwości: jeden dla zestawu DBPROPSET_DATASOURCEINFO i jeden dla zestawu DBPROPSET_DBINIT. Zestaw DBPROPSET_DATASOURCEINFO odpowiada właściwościom dostawcy i jego źródła danych. Zestaw DBPROPSET_DBINIT odpowiada właściwościom używanym podczas inicjacji. Szablony dostawcy OLE DB obsługują te zestawy za pomocą PROPERTY_SET makr. Makra tworzą blok zawierający tablicę właściwości. Za każdym razem, gdy klient wywołuje `IDBProperties` interfejs, Dostawca używa mapy właściwości.

Nie trzeba implementować każdej właściwości w specyfikacji. Należy jednak obsługiwać wymagane właściwości; Aby uzyskać więcej informacji, zobacz specyfikację poziomu 0. Jeśli nie chcesz obsługiwać właściwości, możesz usunąć ją z mapy. Jeśli chcesz obsłużyć właściwość, Dodaj ją do mapy za pomocą makra PROPERTY_INFO_ENTRY. Makro odpowiada `UPROPINFO` strukturze, jak pokazano w poniższym kodzie:

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

Każdy element w strukturze reprezentuje informacje do obsługi właściwości. Zawiera on, `DBPROPID` Aby określić identyfikator GUID i identyfikator właściwości. Zawiera również wpisy określające typ i wartość właściwości.

Jeśli chcesz zmienić wartość domyślną właściwości (należy zauważyć, że konsument może zmienić wartość właściwości zapisywalnej w dowolnym momencie), można użyć makra PROPERTY_INFO_ENTRY_VALUE lub PROPERTY_INFO_ENTRY_EX. Te makra umożliwiają określenie wartości odpowiadającej właściwości. Makro PROPERTY_INFO_ENTRY_VALUE jest notacją skróconą, która pozwala na zmianę wartości. Makro PROPERTY_INFO_ENTRY_VALUE wywołuje PROPERTY_INFO_ENTRY_EX makro. To makro umożliwia dodanie lub zmianę wszystkich atrybutów w `UPROPINFO` strukturze.

Jeśli chcesz zdefiniować własny zestaw właściwości, możesz dodać jeden, tworząc dodatkową kombinację BEGIN_PROPSET_MAP/END_PROPSET_MAP. Zdefiniuj identyfikator GUID dla zestawu właściwości, a następnie zdefiniuj własne właściwości. Jeśli masz właściwości specyficzne dla dostawcy, Dodaj je do nowego zestawu właściwości zamiast przy użyciu istniejącego. Pozwala to uniknąć problemów z nowszymi wersjami OLE DB.

## <a name="user-defined-property-sets"></a>Zestawy właściwości zdefiniowane przez użytkownika

Visual C++ obsługuje zestawy właściwości zdefiniowane przez użytkownika. Nie musisz przesłonić `GetProperties` lub `GetPropertyInfo` . Zamiast tego, szablony wykrywają dowolny zdefiniowany przez użytkownika zestaw właściwości i dodają go do odpowiedniego obiektu.

Jeśli istnieje zestaw właściwości zdefiniowany przez użytkownika, który musi być dostępny w czasie inicjacji (to jest przed wywołaniem konsumenta `IDBInitialize::Initialize` ), można go określić przy użyciu flagi UPROPSET_USERINIT wraz z makrem BEGIN_PROPERTY_SET_EX. Aby to OLE DB działało, zestaw właściwości musi znajdować się w obiekcie źródła danych. Na przykład:

```cpp
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)
```

## <a name="see-also"></a>Zobacz też

[Pliki generowane przez kreatora dostawcy](../../data/oledb/provider-wizard-generated-files.md)<br/>
