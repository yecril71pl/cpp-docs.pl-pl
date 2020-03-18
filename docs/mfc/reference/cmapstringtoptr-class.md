---
title: Klasa CMapStringToPtr
ms.date: 11/04/2016
f1_keywords:
- CMapStringToPtr
- AFXCOLL/CMapStringToPtr
- AFXCOLL/CMapStringToPtr::CMapStringToPtr
- AFXCOLL/CMapStringToPtr::GetCount
- AFXCOLL/CMapStringToPtr::GetHashTableSize
- AFXCOLL/CMapStringToPtr::GetNextAssoc
- AFXCOLL/CMapStringToPtr::GetSize
- AFXCOLL/CMapStringToPtr::GetStartPosition
- AFXCOLL/CMapStringToPtr::HashKey
- AFXCOLL/CMapStringToPtr::InitHashTable
- AFXCOLL/CMapStringToPtr::IsEmpty
- AFXCOLL/CMapStringToPtr::Lookup
- AFXCOLL/CMapStringToPtr::LookupKey
- AFXCOLL/CMapStringToPtr::RemoveAll
- AFXCOLL/CMapStringToPtr::RemoveKey
- AFXCOLL/CMapStringToPtr::SetAt
helpviewer_keywords:
- CMapStringToPtr [MFC], CMapStringToPtr
- CMapStringToPtr [MFC], GetCount
- CMapStringToPtr [MFC], GetHashTableSize
- CMapStringToPtr [MFC], GetNextAssoc
- CMapStringToPtr [MFC], GetSize
- CMapStringToPtr [MFC], GetStartPosition
- CMapStringToPtr [MFC], HashKey
- CMapStringToPtr [MFC], InitHashTable
- CMapStringToPtr [MFC], IsEmpty
- CMapStringToPtr [MFC], Lookup
- CMapStringToPtr [MFC], LookupKey
- CMapStringToPtr [MFC], RemoveAll
- CMapStringToPtr [MFC], RemoveKey
- CMapStringToPtr [MFC], SetAt
ms.assetid: 1ac11143-eb0a-4511-a662-2df0d1d9005b
ms.openlocfilehash: 0e722b305dad6595eb67b1a235c375d21f674353
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442605"
---
# <a name="cmapstringtoptr-class"></a>Klasa CMapStringToPtr

Obsługuje mapy wskaźników typu void, które są oparte na `CString` obiektów.

## <a name="syntax"></a>Składnia

```
class CMapStringToPtr : public CObject
```

## <a name="members"></a>Elementy członkowskie

Funkcje składowe `CMapStringToPtr` są podobne do funkcji składowych klasy [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). W związku z tym podobieństwem można użyć dokumentacji referencyjnej `CMapStringToOb` dla specyficznych dla funkcji składowych. Wszędzie tam, gdzie widzisz wskaźnik `CObject` jako parametr funkcji lub wartość zwracana, Zastąp wskaźnik do typu **void**.

`BOOL CMapStringToPtr::Lookup( LPCTSTR <key>, void*& <rValue> ) const;`

na przykład tłumaczy na

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CMapStringToPtr::CMapStringToPtr](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CMapStringToPtr:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Zwraca liczbę elementów w tej mapie.|
|[CMapStringToPtr::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Określa bieżącą liczbę elementów w tabeli skrótów.|
|[CMapStringToPtr::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Pobiera następny element do iteracji.|
|[CMapStringToPtr:: GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Zwraca liczbę elementów w tej mapie.|
|[CMapStringToPtr::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Zwraca pozycję pierwszego elementu.|
|[CMapStringToPtr::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Oblicza wartość skrótu określonego klucza.|
|[CMapStringToPtr::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicjuje tablicę skrótów.|
|[CMapStringToPtr:: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testuje warunek pustej mapy (nie elementy).|
|[CMapStringToPtr:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Wyszukuje wskaźnik void na podstawie klucza wskaźnika void. Wartość wskaźnika, a nie jednostka, do której wskazuje, jest używana do porównania klucza.|
|[CMapStringToPtr:: LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Zwraca odwołanie do klucza skojarzonego z określoną wartością klucza.|
|[CMapStringToPtr::](../../mfc/reference/cmapstringtoob-class.md#removeall)|Usuwa wszystkie elementy z tej mapy.|
|[CMapStringToPtr::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Usuwa element określony przez klucz.|
|[CMapStringToPtr::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Wstawia element do mapy; Zastępuje istniejący element, jeśli zostanie znaleziony pasujący klucz.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CMapStringToPtr:: operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Wstawia element do mapy — podstawienie operatora dla `SetAt`.|

## <a name="remarks"></a>Uwagi

`CMapStringToPtr` obejmuje makro IMPLEMENT_DYNAMIC w celu obsługi dostępu do typu w czasie wykonywania i zatopienia do obiektu `CDumpContext`. Jeśli potrzebujesz zrzutu poszczególnych elementów mapy, należy ustawić głębokość kontekstu zrzutu na 1 lub większą.

Mapowania ciągów do wskaźnika nie mogą być serializowane.

Po usunięciu obiektu `CMapStringToPtr` lub po usunięciu jego elementów obiekty kluczy `CString` i słowa zostaną usunięte.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToPtr`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll. h

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
