---
title: Klasa CMapWordToOb
ms.date: 11/04/2016
f1_keywords:
- CMapWordToOb
- AFXCOLL/CMapWordToOb
- AFXCOLL/CMapWordToOb::CMapWordToOb
- AFXCOLL/CMapWordToOb::GetCount
- AFXCOLL/CMapWordToOb::GetHashTableSize
- AFXCOLL/CMapWordToOb::GetNextAssoc
- AFXCOLL/CMapWordToOb::GetSize
- AFXCOLL/CMapWordToOb::GetStartPosition
- AFXCOLL/CMapWordToOb::HashKey
- AFXCOLL/CMapWordToOb::InitHashTable
- AFXCOLL/CMapWordToOb::IsEmpty
- AFXCOLL/CMapWordToOb::Lookup
- AFXCOLL/CMapWordToOb::LookupKey
- AFXCOLL/CMapWordToOb::RemoveAll
- AFXCOLL/CMapWordToOb::RemoveKey
- AFXCOLL/CMapWordToOb::SetAt
helpviewer_keywords:
- CMapWordToOb [MFC], CMapWordToOb
- CMapWordToOb [MFC], GetCount
- CMapWordToOb [MFC], GetHashTableSize
- CMapWordToOb [MFC], GetNextAssoc
- CMapWordToOb [MFC], GetSize
- CMapWordToOb [MFC], GetStartPosition
- CMapWordToOb [MFC], HashKey
- CMapWordToOb [MFC], InitHashTable
- CMapWordToOb [MFC], IsEmpty
- CMapWordToOb [MFC], Lookup
- CMapWordToOb [MFC], LookupKey
- CMapWordToOb [MFC], RemoveAll
- CMapWordToOb [MFC], RemoveKey
- CMapWordToOb [MFC], SetAt
ms.assetid: 9c9bcd76-456f-4cf9-b03c-dd28b49d5e4f
ms.openlocfilehash: 80d53f195ba98f853c86a4d9c38fa9fcda52da3b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442586"
---
# <a name="cmapwordtoob-class"></a>Klasa CMapWordToOb

Obsługuje mapy wskaźników `CObject`, które są oparte na słowach 16-bitowych.

## <a name="syntax"></a>Składnia

```
class CMapWordToOb : public CObject
```

## <a name="members"></a>Elementy członkowskie

Funkcje składowe `CMapWordToOb` są podobne do funkcji składowych klasy [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). W związku z tym podobieństwem można użyć dokumentacji referencyjnej `CMapStringToOb` dla specyficznych dla funkcji składowych. Wszędzie tam, gdzie widzisz `CString` lub **stały wskaźnik do** **char** jako parametr funkcji lub wartość zwracaną, podstaw wyraz.

`BOOL CMapWordToOb::Lookup( WORD <key>, CObject*& <rValue> ) const;`

na przykład tłumaczy na

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CMapWordToOb::CMapWordToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CMapWordToOb:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Zwraca liczbę elementów w tej mapie.|
|[CMapWordToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Określa bieżącą liczbę elementów w tabeli skrótów.|
|[CMapWordToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Pobiera następny element do iteracji.|
|[CMapWordToOb:: GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Zwraca liczbę elementów w tej mapie.|
|[CMapWordToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Zwraca pozycję pierwszego elementu.|
|[CMapWordToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Oblicza wartość skrótu określonego klucza.|
|[CMapWordToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicjuje tablicę skrótów.|
|[CMapWordToOb:: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testuje warunek pustej mapy (nie elementy).|
|[CMapWordToOb:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Wyszukuje wskaźnik void na podstawie klucza wskaźnika void. Wartość wskaźnika, a nie jednostka, do której wskazuje, jest używana do porównania klucza.|
|[CMapWordToOb:: LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Zwraca odwołanie do klucza skojarzonego z określoną wartością klucza.|
|[CMapWordToOb::](../../mfc/reference/cmapstringtoob-class.md#removeall)|Usuwa wszystkie elementy z tej mapy.|
|[CMapWordToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Usuwa element określony przez klucz.|
|[CMapWordToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Wstawia element do mapy; Zastępuje istniejący element, jeśli zostanie znaleziony pasujący klucz.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CMapWordToOb:: operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Wstawia element do mapy — podstawienie operatora dla `SetAt`.|

## <a name="remarks"></a>Uwagi

`CMapWordToOb` zawiera IMPLEMENT_SERIAL makro do obsługi serializacji i dumpingu jego elementów. Każdy element jest serializowany, jeśli mapa jest przechowywana w archiwum, za pomocą operatora przeciążonego wstawiania ( **<<** ) lub funkcji członkowskiej `Serialize`.

Jeśli potrzebujesz zrzutu poszczególnych elementów WYRAZów `CObject`, musisz ustawić głębokość kontekstu zrzutu na 1 lub większą.

Po usunięciu obiektu `CMapWordToOb` lub po usunięciu jego elementów, wskaźniki `CObject` są usuwane. Obiekty, do których odwołuje się wskaźniki `CObject`, nie są niszczone.

Aby uzyskać więcej informacji na temat `CMapWordToOb`, zobacz [kolekcje](../../mfc/collections.md)artykułów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CMapWordToOb`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll. h

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
