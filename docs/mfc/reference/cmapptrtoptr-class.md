---
title: CMapPtrToPtr Class
ms.date: 11/04/2016
f1_keywords:
- CMapPtrToPtr
- AFXCOLL/CMapPtrToPtr
- AFXCOLL/CMapPtrToPtr::CMapPtrToPtr
- AFXCOLL/CMapPtrToPtr::GetCount
- AFXCOLL/CMapPtrToPtr::GetHashTableSize
- AFXCOLL/CMapPtrToPtr::GetNextAssoc
- AFXCOLL/CMapPtrToPtr::GetSize
- AFXCOLL/CMapPtrToPtr::GetStartPosition
- AFXCOLL/CMapPtrToPtr::HashKey
- AFXCOLL/CMapPtrToPtr::InitHashTable
- AFXCOLL/CMapPtrToPtr::IsEmpty
- AFXCOLL/CMapPtrToPtr::Lookup
- AFXCOLL/CMapPtrToPtr::LookupKey
- AFXCOLL/CMapPtrToPtr::RemoveAll
- AFXCOLL/CMapPtrToPtr::RemoveKey
- AFXCOLL/CMapPtrToPtr::SetAt
helpviewer_keywords:
- CMapPtrToPtr [MFC], CMapPtrToPtr
- CMapPtrToPtr [MFC], GetCount
- CMapPtrToPtr [MFC], GetHashTableSize
- CMapPtrToPtr [MFC], GetNextAssoc
- CMapPtrToPtr [MFC], GetSize
- CMapPtrToPtr [MFC], GetStartPosition
- CMapPtrToPtr [MFC], HashKey
- CMapPtrToPtr [MFC], InitHashTable
- CMapPtrToPtr [MFC], IsEmpty
- CMapPtrToPtr [MFC], Lookup
- CMapPtrToPtr [MFC], LookupKey
- CMapPtrToPtr [MFC], RemoveAll
- CMapPtrToPtr [MFC], RemoveKey
- CMapPtrToPtr [MFC], SetAt
ms.assetid: 23cbbaec-9d64-48f2-92ae-5e24fa64b926
ms.openlocfilehash: b4ae511caab8278daf723bbcb8ffc5d57f5a1cd0
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442673"
---
# <a name="cmapptrtoptr-class"></a>CMapPtrToPtr Class

Obsługuje mapy wskaźników typu void, które są oparte na wskaźnikach void.

## <a name="syntax"></a>Składnia

```
class CMapPtrToPtr : public CObject
```

## <a name="members"></a>Elementy członkowskie

Funkcje składowe `CMapPtrToPtr` są podobne do funkcji składowych klasy [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). W związku z tym podobieństwem można użyć dokumentacji referencyjnej `CMapStringToOb` dla specyficznych dla funkcji składowych. Wszędzie tam, gdzie widzisz wskaźnik `CObject` jako parametr funkcji lub wartość zwracana, Zastąp wskaźnik do typu **void**. Wszędzie tam, gdzie widzisz `CString` lub **stały wskaźnik do** **char** jako parametr funkcji lub wartość zwracana, Zastąp wskaźnik do typu **void**.

`BOOL CMapPtrToPtr::Lookup( void* <key>, void*& <rValue> ) const;`

na przykład tłumaczy na

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CMapPtrToPtr::CMapPtrToPtr](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CMapPtrToPtr:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Zwraca liczbę elementów w tej mapie.|
|[CMapPtrToPtr::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Określa bieżącą liczbę elementów w tabeli skrótów.|
|[CMapPtrToPtr::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Pobiera następny element do iteracji.|
|[CMapPtrToPtr:: GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Zwraca liczbę elementów w tej mapie.|
|[CMapPtrToPtr::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Zwraca pozycję pierwszego elementu.|
|[CMapPtrToPtr::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Oblicza wartość skrótu określonego klucza.|
|[CMapPtrToPtr::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicjuje tablicę skrótów.|
|[CMapPtrToPtr:: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Testuje warunek pustej mapy (nie elementy).|
|[CMapPtrToPtr:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Wyszukuje wskaźnik void na podstawie klucza wskaźnika void. Wartość wskaźnika, a nie jednostka, do której wskazuje, jest używana do porównania klucza.|
|[CMapPtrToPtr:: LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Zwraca odwołanie do klucza skojarzonego z określoną wartością klucza.|
|[CMapPtrToPtr::](../../mfc/reference/cmapstringtoob-class.md#removeall)|Usuwa wszystkie elementy z tej mapy.|
|[CMapPtrToPtr::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Usuwa element określony przez klucz.|
|[CMapPtrToPtr::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Wstawia element do mapy; Zastępuje istniejący element, jeśli zostanie znaleziony pasujący klucz.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CMapPtrToPtr:: operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Wstawia element do mapy — podstawienie operatora dla `SetAt`.|

## <a name="remarks"></a>Uwagi

`CMapPtrToPtr` obejmuje makro IMPLEMENT_DYNAMIC w celu obsługi dostępu do typu w czasie wykonywania i zatopienia do obiektu `CDumpContext`. Jeśli potrzebujesz zrzutu poszczególnych elementów mapy (wartości wskaźnika), musisz ustawić głębokość kontekstu zrzutu na 1 lub większą.

Mapowania wskaźnika do wskaźnika nie mogą być serializowane.

Po usunięciu obiektu `CMapPtrToPtr` lub po usunięciu jego elementów zostaną usunięte tylko te wskaźniki, a nie jednostki, do których się odwołują.

Aby uzyskać więcej informacji na temat `CMapPtrToPtr`, zobacz [kolekcje](../../mfc/collections.md)artykułów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CMapPtrToPtr`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll. h

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
