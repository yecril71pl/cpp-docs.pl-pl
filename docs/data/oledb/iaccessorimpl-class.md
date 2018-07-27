---
title: Iaccessorimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IAccessorImpl
- ATL.IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::IAccessorImpl
- IAccessorImpl::IAccessorImpl
- IAccessorImpl.IAccessorImpl
- IAccessorImpl
- ATL::IAccessorImpl::AddRefAccessor
- AddRefAccessor
- IAccessorImpl::AddRefAccessor
- IAccessorImpl.AddRefAccessor
- ATL.IAccessorImpl.AddRefAccessor
- IAccessorImpl::CreateAccessor
- CreateAccessor
- ATL::IAccessorImpl::CreateAccessor
- IAccessorImpl.CreateAccessor
- ATL.IAccessorImpl.CreateAccessor
- IAccessorImpl.GetBindings
- ATL::IAccessorImpl::GetBindings
- IAccessorImpl::GetBindings
- GetBindings
- ATL.IAccessorImpl.GetBindings
- ReleaseAccessor
- IAccessorImpl::ReleaseAccessor
- ATL.IAccessorImpl.ReleaseAccessor
- ATL::IAccessorImpl::ReleaseAccessor
- IAccessorImpl.ReleaseAccessor
dev_langs:
- C++
helpviewer_keywords:
- IAccessorImpl class
- IAccessorImpl class, constructor
- IAccessorImpl constructor
- AddRefAccessor method
- CreateAccessor method
- GetBindings method
- ReleaseAccessor method
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0ac22d8ee45209ad6a20dcb34a75c06dd9b80b58
ms.sourcegitcommit: b0d6777cf4b580d093eaf6104d80a888706e7578
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39269891"
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl — Klasa
Udostępnia implementację [IAccessor](https://msdn.microsoft.com/library/ms719672.aspx) interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class T, 
          class BindType = ATLBINDINGS,
          class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>  
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Klasy obiektu zestawu wierszy lub polecenie.  
  
 *BindType*  
 Jednostki magazynu, aby uzyskać informacje o powiązaniu. Wartość domyślna to `ATLBINDINGS` struktury (patrz atldb.h).  
  
 *BindingVector*  
 Jednostki magazynu na potrzeby informacji o kolumnie. Wartość domyślna to [CAtlMap](../../atl/reference/catlmap-class.md) którym kluczowy element jest wartością HACCESSOR i element wartości jest wskaźnikiem do `BindType` struktury.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  

## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Iaccessorimpl —](#iaccessorimpl)|Konstruktor.|  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[AddRefAccessor](#addrefaccessor)|Dodaje licznik odwołań do istniejącej metody dostępu.|  
|[CreateAccessor](#createaccessor)|Tworzy metodę dostępu na podstawie zestawu powiązania.|  
|[Getbindings —](#getbindings)|Zwraca powiązania w metodzie dostępu.|  
|[ReleaseAccessor](#releaseaccessor)|Udostępnia metody dostępu.|  
  
## <a name="remarks"></a>Uwagi  
 Jest to parametr obowiązkowy dla polecenia i zestawy wierszy. OLE DB wymaga dostawców w celu zaimplementowania HACCESSOR, czyli tag do tablicy [DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx) struktury. Dostarczone przez HACCESSORs `IAccessorImpl` są adresy `BindType` struktury. Domyślnie `BindType` jest zdefiniowany jako `ATLBINDINGS` w `IAccessorImpl`w definicji szablonu. `BindType` udostępnia mechanizm używany przez `IAccessorImpl` śledzić liczbę elementów w jego `DBBINDING` tablicy, a także flagi metody dostępu i liczba odwołań.  

## <a name="iaccessorimpl"></a> IAccessorImpl::IAccessorImpl
Konstruktor.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
IAccessorImpl();  
  
```  

## <a name="addrefaccessor"></a> IAccessorImpl::AddRefAccessor
Dodaje licznik odwołań do istniejącej metody dostępu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD(AddRefAccessor)(HACCESSOR hAccessor,  
   DBREFCOUNT* pcRefCount);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IAccessor::AddRefAccessor](https://msdn.microsoft.com/library/ms714978.aspx) w *OLE DB Podręcznik programisty*.

## <a name="createaccessor"></a> IAccessorImpl::CreateAccessor
Tworzy metodę dostępu na podstawie zestawu powiązania.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD(CreateAccessor)(DBACCESSORFLAGS dwAccessorFlags,  
   DBCOUNTITEM cBindings,  
   const DBBINDING rgBindings[],  
   DBLENGTH cbRowSize,  
   HACCESSOR* phAccessor,  
   DBBINDSTATUS rgStatus[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IAccessor::CreateAccessor](https://msdn.microsoft.com/library/ms720969.aspx) w *OLE DB Podręcznik programisty*.  

## <a name="getbindings"></a> IAccessorImpl::GetBindings
Zwraca powiązania kolumny podstawowe od konsumenta w metodzie dostępu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD(GetBindings)(HACCESSOR hAccessor,  
   DBACCESSORFLAGS* pdwAccessorFlags,  
   DBCOUNTITEM* pcBindings,  
   DBBINDING** prgBindings);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IAccessor::GetBindings](https://msdn.microsoft.com/library/ms721253.aspx) w *OLE DB Podręcznik programisty*. 

## <a name="releaseaccessor"></a> IAccessorImpl::ReleaseAccessor
Udostępnia metody dostępu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD(ReleaseAccessor)(HACCESSOR hAccessor,  
   DBREFCOUNT* pcRefCount);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IAccessor::ReleaseAccessor](https://msdn.microsoft.com/library/ms719717.aspx) w *OLE DB Podręcznik programisty*.
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
