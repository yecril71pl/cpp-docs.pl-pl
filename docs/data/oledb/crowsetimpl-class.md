---
title: "Crowsetimpl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowsetImpl
- ATL.CRowsetImpl
- ATL::CRowsetImpl
dev_langs:
- C++
helpviewer_keywords:
- CRowsetImpl class
ms.assetid: e97614b3-b11d-4806-a0d3-b9401331473f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c126c757ae4776d0b2a5d2bec352ee8d58c4f0d4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="crowsetimpl-class"></a>CRowsetImpl — Klasa
Udostępnia standardowej implementacji zestawu wierszy OLE DB bez konieczności dziedziczenie wielokrotne wiele implementacji interfejsów.  
  
## <a name="syntax"></a>Składnia

```cpp
template <  
   class T,  
   class Storage,  
   class CreatorClass,  
   class ArrayType = CAtlArray<Storage>,   
   class RowClass = CSimpleRow,   
   class RowsetInterface = IRowsetImpl <T, IRowset>   
>  
class CRowsetImpl :    
   public CComObjectRootEx<CreatorClass::_ThreadModel>,   
   public CRowsetBaseImpl<T, Storage, ArrayType, RowsetInterface>,   
   public IRowsetInfoImpl<T, CreatorClass::_PropClass>  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasa użytkownika, która jest pochodną `CRowsetImpl`.  
  
 `Storage`  
 Klasa rekordu użytkownika.  
  
 `CreatorClass`  
 Klasa, która zawiera właściwości dla zestawu wierszy; Zazwyczaj polecenia.  
  
 `ArrayType`  
 Klasa, która będzie działać jako magazyn dla zestawu wierszy danych. Wartością domyślną tego parametru `CAtlArray`, ale może być dowolnej klasy, która obsługuje wymaganej funkcjonalności.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[NameFromDBID](../../data/oledb/crowsetimpl-namefromdbid.md)|Wyodrębnia ciągu z **DBID** i kopiuje go do `bstr` przekazany.|  
|[SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)|Weryfikuje i przechowuje **DBID**s w dwóch ciągów ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).|  
  
### <a name="overridable-methods"></a>Nadpisywalnych metod  
  
|||  
|-|-|  
|[GetColumnInfo](../../data/oledb/crowsetimpl-getcolumninfo.md)|Pobiera informacje dotyczące kolumn dla żądania określonego klienta.|  
|[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)|Sprawdza, jeśli jeden lub oba parametry nie zawierają wartości ciągu, a jeśli tak, kopiuje wartości ciągu do elementów członkowskich danych [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|  
|[ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)|Sprawdza, aby zobaczyć, czy w jednej lub obu **DBID**s zawierają wartości ciągu, a jeśli tak, kopiuje je do jego elementów członkowskich danych [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)|Domyślnie `CAtlArray` który templatizes na argumencie szablonu rekordu użytkownika, aby `CRowsetImpl`. Innej klasy typu tablicy mogą być używane przez zmianę `ArrayType` argumentu szablonu dla `CRowsetImpl`.|  
|[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)|Zawiera polecenie początkowego zestawu wierszy.|  
|[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)|Zawiera indeks początkowego zestawu wierszy.|  
  
## <a name="remarks"></a>Uwagi  
 `CRowsetImpl` udostępnia zastąpień w formie upcasts statycznych. Metody kontrolowania sposobu, w którym danego zestawu wierszy zostanie Walidacja tekstu polecenia. Utwórz swój własny `CRowsetImpl`— styl klasy dzięki implementacji interfejsów dziedziczone wielu. Jedyną metodą, dla której należy podać implementacja jest **Execute**. W zależności od tego, jakiego rodzaju zestawu wierszy jest tworzony, metody creator będzie oczekiwać na różnych podpisów dla **Execute**. Na przykład, jeśli używasz `CRowsetImpl`-klasy do zaimplementowania zestawu wierszy schematu **Execute** metoda ma następującą sygnaturą:  
  
 `HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`  
  
 Jeśli tworzysz `CRowsetImpl`-klasy do zaimplementowania polecenia lub wierszy sesji **Execute** metoda ma następującą sygnaturą:  
  
 `HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`  
  
 Do wykonania tych `CRowsetImpl`-pochodnych **Execute** metod, należy wypełnić Twojej buforów danych wewnętrznych ([m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h