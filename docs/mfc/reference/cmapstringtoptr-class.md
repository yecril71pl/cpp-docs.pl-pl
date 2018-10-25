---
title: Klasa CMapStringToPtr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc7d201ba32d0f7e3a4c860c6df117e9c74ae254
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055505"
---
# <a name="cmapstringtoptr-class"></a>Klasa CMapStringToPtr

Obsługuje mapy wskaźników typu void opartych na kluczach przez `CString` obiektów.

## <a name="syntax"></a>Składnia

```
class CMapStringToPtr : public CObject
```

## <a name="members"></a>Elementy członkowskie

Funkcje elementów członkowskich `CMapStringToPtr` są podobne do funkcji elementów członkowskich klasy [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Ze względu na to podobieństwa można użyć `CMapStringToOb` dokumentacji kątem specyfiki funkcja elementu członkowskiego. Po wyświetleniu `CObject` wskaźnik jako funkcja parametru lub zwracanej wartości, Wstaw wskaźnik do **void**.

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

na przykład przekłada się na

`BOOL CMapStringToPtr::Lookup( LPCTSTR <key>, void*& <rValue> ) const;`

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMapStringToOb::CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMapStringToOb::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Zwraca liczbę elementów na tej mapie.|
|[CMapStringToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Określa aktualną liczbę elementów w tabeli wyznaczania wartości skrótu.|
|[CMapStringToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Pobiera następny element do wykonania iteracji.|
|[CMapStringToOb::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Zwraca liczbę elementów na tej mapie.|
|[CMapStringToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Zwraca pozycję pierwszego elementu.|
|[CMapStringToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Oblicza wartość skrótu dla określonego klucza.|
|[CMapStringToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicjuje tabelę mieszania.|
|[CMapStringToOb::IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testuje pod kątem warunku pusta Mapa (Brak elementów).|
|[CMapStringToOb::Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Wyszukuje wskaźnika void oparte na kluczu wskaźnika void. Wartość wskaźnika, a nie jednostki, który wskazuje, służy do porównywania kluczy.|
|[CMapStringToOb::LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Zwraca odwołanie do klucz skojarzony z określoną wartością klucza.|
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Usuwa wszystkie elementy z tej mapie.|
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Usuwa element określony przez klucz.|
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Wstawia element do mapy; zastępuje istniejący element, jeśli dopasowany klucz zostanie znaleziony.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[[] CMapStringToOb::operator](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Wstawia element do mapy — operator podstawienia dla `SetAt`.|

## <a name="remarks"></a>Uwagi

`CMapStringToPtr` dołącza IMPLEMENT_DYNAMIC — makro do obsługi dostępu typu run-time i zrzucanie `CDumpContext` obiektu. Zrzut mapy poszczególnych elementów, należy należy ustawić głębokość kontekstu zrzutu do 1 lub większą.

Mapy wskaźnika ciągu nie może być serializowany.

Gdy `CMapStringToPtr` obiekt zostanie usunięty lub gdy jego elementy są usuwane, `CString` obiektów kluczy i wyrazy są usuwane.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToPtr`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll.h

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)

