---
title: CMyProviderSource (MyProviderDS.H) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- myproviderds.h
- cmyprovidersource
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderSource class in MyProviderDS.H
ms.assetid: c143d48e-59c8-4f67-9141-3aab51859b92
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f141ad7565a78ff4e7a02b3847287879b81ccd6d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cmyprovidersource-myproviderdsh"></a>CMyProviderSource (MyProviderDS.H)
Dziedziczenie wielokrotne za pomocą klasy dostawcy. Poniższy kod przedstawia łańcuch dziedziczenia dla obiekt źródła danych:  
  
```cpp
/////////////////////////////////////////////////////////////////////////  
// CMyProviderSource  
class ATL_NO_VTABLE CMyProviderSource :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public CComCoClass<CMyProviderSource, &CLSID_MyProvider>,  
   public IDBCreateSessionImpl<CMyProviderSource, CMyProviderSession>,  
   public IDBInitializeImpl<CMyProviderSource>,  
   public IDBPropertiesImpl<CMyProviderSource>,  
   public IPersistImpl<CMyProviderSource>,  
   public IInternalConnectionImpl<CMyProviderSource>  
```  
  
 Wszystkie składniki COM pochodzi od `CComObjectRootEx` i `CComCoClass`. `CComObjectRootEx` zawiera wszystkie wdrożenia dla **IUnknown** interfejsu. Może obsługiwać żadnych modelu wątkowości. `CComCoClass` obsługuje wszelkie wymagane wsparcie błędu. Jeśli chcesz wysłać bardziej rozbudowane informacje o błędzie do klienta, można użyć pewnych błąd interfejsów API w `CComCoClass`.  
  
 Obiekt źródła danych dziedziczy również kilka klas "Impl". Każda klasa zawiera implementację interfejsu. Źródło danych implementuje obiektu `IPersist`, `IDBProperties`, **IDBInitialize**, i **IDBCreateSession** interfejsów. Każdy interfejs jest wymagany przez OLE DB do zaimplementowania obiektu źródła danych. Istnieje możliwość obsługi lub nie obsługuje funkcji określonego przez dziedziczenie ani nie dziedziczy z jednej z tych klas "Impl". Jeśli chcesz obsługiwać **IDBDataSourceAdmin** interfejsu, dziedziczą z **IDBDataSourceAdminImpl** klasę, aby korzystać z funkcji wymagane.  
  
## <a name="com-map"></a>Mapa modelu COM  
 Zawsze, gdy klient wywołuje `QueryInterface` interfejsu w źródle danych, przechodzi ona przez następujące mapie modelu COM:  
  
```  
BEGIN_COM_MAP(CMyProviderSource)  
   COM_INTERFACE_ENTRY(IDBCreateSession)  
   COM_INTERFACE_ENTRY(IDBInitialize)  
   COM_INTERFACE_ENTRY(IDBProperties)  
   COM_INTERFACE_ENTRY(IPersist)  
   COM_INTERFACE_ENTRY(IInternalConnection)  
END_COM_MAP()  
```  
  
 Makra com_interface_entry — pochodzą z biblioteki ATL i poinformuj wykonania `QueryInterface` w `CComObjectRootEx` do zwrócenia odpowiednich interfejsów.  
  
## <a name="property-map"></a>Mapy właściwości  
 Mapy właściwości określa wszystkie właściwości wskazywany przez dostawcę:  
  
```  
BEGIN_PROPSET_MAP(CMyProviderSource)  
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
   CHAIN_PROPERTY_SET(CMyProviderSession)  
END_PROPSET_MAP()  
```  
  
 Właściwości w bazie danych OLE DB są grupowane. Obiekt źródła danych ma dwie grupy właściwości: jeden dla **DBPROPSET_DATASOURCEINFO** zestaw i jeden dla **DBPROPSET_DBINIT** ustawiony. **DBPROPSET_DATASOURCEINFO** zestaw odnosi się do właściwości o dostawcy i źródła danych. **DBPROPSET_DBINIT** odpowiada zestaw właściwości używanych podczas inicjowania. Szablony OLE DB Provider obsługiwać te zestawy za pomocą makra PROPERTY_SET. Makra utworzyć bloku, który zawiera tablicę właściwości. Zawsze, gdy klient wywołuje `IDBProperties` interfejs, dostawca używa właściwości mapy.  
  
 Nie należy do implementacji dla każdej właściwości w specyfikacji. Jednak musi obsługiwać wymagane właściwości; zobacz specyfikację zgodność poziom 0, aby uzyskać więcej informacji. Jeśli nie obsługuje właściwości, można go usunąć z mapy. Jeśli chcesz obsługuje właściwości, dodaj ją do mapy przy użyciu PROPERTY_INFO_ENTRY — makro. Makro odpowiada **UPROPINFO** struktury, jak pokazano w poniższym kodzie:  
  
```  
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
  
 Każdy element w strukturze reprezentuje informacje do obsługi właściwości. Zawiera on **DBPROPID** Aby określić identyfikator GUID i identyfikator właściwości. Zawiera ona także pozycje, aby określić typ i wartość właściwości.  
  
 Jeśli chcesz zmienić domyślną wartość właściwości (Uwaga konsumenta można zmienić wartości właściwości z możliwością zapisu w dowolnym momencie), można użyć makra PROPERTY_INFO_ENTRY_VALUE albo PROPERTY_INFO_ENTRY_EX. Makra te umożliwiają określenie wartości odpowiednich właściwości. PROPERTY_INFO_ENTRY_VALUE — makro jest skróconej notacji, która pozwala na zmianę wartości. PROPERTY_INFO_ENTRY_VALUE — makro wywołuje PROPERTY_INFO_ENTRY_EX — makro. To makro umożliwia dodawanie lub zmienianie wszystkie atrybuty w **UPROPINFO** struktury.  
  
 Jeśli chcesz zdefiniować własny zestaw właściwości, możesz dodać kategorię, wprowadzając dodatkowe kombinacja BEGIN_PROPSET_MAP/END_PROPSET_MAP. Należy określić identyfikator GUID dla zestawu właściwości, a następnie zdefiniuj własnych właściwości. Jeśli masz właściwości specyficznych dla dostawcy, dodaj je do nową właściwość, ustaw zamiast za pomocą jednego z istniejących. Dzięki temu można uniknąć problemów w nowszych wersjach OLE DB.  
  
## <a name="user-defined-property-sets"></a>Zestawy właściwości zdefiniowane przez użytkownika  
 Visual C++ obsługuje zestawy właściwości zdefiniowane przez użytkownika. Nie masz do przesłonięcia **GetProperties** lub `GetPropertyInfo`. Zamiast tego szablony wykryć żadnych zestaw właściwości zdefiniowane przez użytkownika i dodaj go do odpowiedniego obiektu.  
  
 Jeśli masz zestaw właściwości zdefiniowane przez użytkownika, który musi być dostępny w czasie inicjowania (oznacza to, zanim klient wywołuje **IDBInitialize::Initialize**), można to określić za pomocą **UPROPSET_USERINIT** flagi w połączeniu z BEGIN_PROPERTY_SET_EX — makro. Zestaw właściwości musi należeć do obiektu źródła danych, aby to zrobić (zgodnie ze specyfikacją OLE DB wymaga). Na przykład:  
  
```  
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)  
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)  
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki dostawcy generowane przez kreatora](../../data/oledb/provider-wizard-generated-files.md)