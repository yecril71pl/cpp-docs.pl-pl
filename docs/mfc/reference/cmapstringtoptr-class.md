---
title: Klasa CMapStringToPtr | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMapStringToPtr
- AFXCOLL/CMapStringToPtr
- AFXCOLL/CMapStringToOb::CMapStringToOb
- AFXCOLL/CMapStringToOb::GetCount
- AFXCOLL/CMapStringToOb::GetHashTableSize
- AFXCOLL/CMapStringToOb::GetNextAssoc
- AFXCOLL/CMapStringToOb::GetSize
- AFXCOLL/CMapStringToOb::GetStartPosition
- AFXCOLL/CMapStringToOb::HashKey
- AFXCOLL/CMapStringToOb::InitHashTable
- AFXCOLL/CMapStringToOb::IsEmpty
- AFXCOLL/CMapStringToOb::Lookup
- AFXCOLL/CMapStringToOb::LookupKey
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CMapStringToOb [MFC], CMapStringToOb
- CMapStringToOb [MFC], GetCount
- CMapStringToOb [MFC], GetHashTableSize
- CMapStringToOb [MFC], GetNextAssoc
- CMapStringToOb [MFC], GetSize
- CMapStringToOb [MFC], GetStartPosition
- CMapStringToOb [MFC], HashKey
- CMapStringToOb [MFC], InitHashTable
- CMapStringToOb [MFC], IsEmpty
- CMapStringToOb [MFC], Lookup
- CMapStringToOb [MFC], LookupKey
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: 1ac11143-eb0a-4511-a662-2df0d1d9005b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 61550a6477a05ee387ecb4e78d6e325e8e74672b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmapstringtoptr-class"></a>Klasa CMapStringToPtr
Obsługuje mapy wskaźniki typu void, wyznaczaną przez `CString` obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMapStringToPtr : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
 Funkcje Członkowskie `CMapStringToPtr` są podobne do funkcji Członkowskich klasy [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Ze względu na to podobieństwa, można użyć `CMapStringToOb` odwołania dokumentacji charakterystykę funkcja elementu członkowskiego. Po wyświetleniu `CObject` wskaźnika jako parametr funkcji lub wartości zwracanej, Zastąp wskaźnik do `void`.  
  
 `BOOL CMapStringToOb::Lookup( const char* <key>,`  
  
 `CObject*& <rValue> ) const;`  
  
 na przykład umożliwia to  
  
 `BOOL CMapStringToPtr::Lookup( LPCTSTR <key>, void*& <rValue> )`  
  
 `const;`  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMapStringToOb::CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMapStringToOb::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Zwraca liczbę elementów na tej mapie.|  
|[CMapStringToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Określa bieżąca liczba elementów w tablicy skrótów.|  
|[CMapStringToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Pobiera następnego elementu potrzeby iteracji.|  
|[CMapStringToOb::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Zwraca liczbę elementów na tej mapie.|  
|[CMapStringToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Zwraca pozycję pierwszego elementu.|  
|[CMapStringToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Oblicza wartość skrótu z określonym kluczem.|  
|[CMapStringToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicjuje tablicy skrótów.|  
|[CMapStringToOb::IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testy dla warunku pusta Mapa (Brak elementów).|  
|[CMapStringToOb::Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Wyszukuje void wskaźnik oparte na kluczu wskaźnika typu void. Wartość wskaźnika, nie jednostki, który wskazuje, służy do porównywania klucza.|  
|[CMapStringToOb::LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Zwraca odwołanie do klucz skojarzony z określoną wartością klucza.|  
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Usuwa wszystkie elementy z tej mapy.|  
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Usuwa element określony przez klucz.|  
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Wstawia element do mapy; zastępuje istniejący element, jeśli dopasowany klucz zostanie znaleziony.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[[CMapStringToOb::operator]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Wstawia element do mapy — operator podstawienia dla `SetAt`.|  
  
## <a name="remarks"></a>Uwagi  
 `CMapStringToPtr`zawiera `IMPLEMENT_DYNAMIC` makro do obsługi dostępu typu run-time i zrzucanie `CDumpContext` obiektu. Zrzut mapy poszczególnych elementów, należy do co najmniej 1 należy ustawić głębokość kontekstu zrzutu.  
  
 Wskaźnik ciągu mapy nie może być serializowany.  
  
 Gdy `CMapStringToPtr` obiekt jest usunięty lub gdy jego elementy są usuwane, `CString` obiektów kluczy i wyrazy są usuwane.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToPtr`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcoll.h  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



