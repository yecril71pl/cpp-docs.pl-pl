---
title: Klasa CUIntArray
ms.date: 11/04/2016
f1_keywords:
- CUIntArray
- AFXCOLL/CUIntArray
- AFXCOLL/CUIntArray::CUIntArray
- AFXCOLL/CUIntArray::Add
- AFXCOLL/CUIntArray::Append
- AFXCOLL/CUIntArray::Copy
- AFXCOLL/CUIntArray::ElementAt
- AFXCOLL/CUIntArray::FreeExtra
- AFXCOLL/CUIntArray::GetAt
- AFXCOLL/CUIntArray::GetCount
- AFXCOLL/CUIntArray::GetData
- AFXCOLL/CUIntArray::GetSize
- AFXCOLL/CUIntArray::GetUpperBound
- AFXCOLL/CUIntArray::InsertAt
- AFXCOLL/CUIntArray::IsEmpty
- AFXCOLL/CUIntArray::RemoveAll
- AFXCOLL/CUIntArray::RemoveAt
- AFXCOLL/CUIntArray::SetAt
- AFXCOLL/CUIntArray::SetAtGrow
- AFXCOLL/CUIntArray::SetSize
helpviewer_keywords:
- CUIntArray [MFC], CUIntArray
- CUIntArray [MFC], Add
- CUIntArray [MFC], Append
- CUIntArray [MFC], Copy
- CUIntArray [MFC], ElementAt
- CUIntArray [MFC], FreeExtra
- CUIntArray [MFC], GetAt
- CUIntArray [MFC], GetCount
- CUIntArray [MFC], GetData
- CUIntArray [MFC], GetSize
- CUIntArray [MFC], GetUpperBound
- CUIntArray [MFC], InsertAt
- CUIntArray [MFC], IsEmpty
- CUIntArray [MFC], RemoveAll
- CUIntArray [MFC], RemoveAt
- CUIntArray [MFC], SetAt
- CUIntArray [MFC], SetAtGrow
- CUIntArray [MFC], SetSize
ms.assetid: d71f3d8f-ef9f-4e48-9b69-7782c0e2ddf7
ms.openlocfilehash: 932062ec289a34cffcd929853233a0c7c81a7a72
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447541"
---
# <a name="cuintarray-class"></a>Klasa CUIntArray

Obsługuje tablice liczb całkowitych bez znaku.

## <a name="syntax"></a>Składnia

```
class CUIntArray : public CObject
```

## <a name="members"></a>Elementy członkowskie

Funkcje składowe `CUIntArray` są podobne do funkcji składowych klasy [CObArray](../../mfc/reference/cobarray-class.md). W związku z tym podobieństwem można użyć dokumentacji referencyjnej `CObArray` dla specyficznych dla funkcji składowych. W każdym przypadku, gdy widzisz wskaźnik `CObject` jako parametr funkcji lub wartość zwrotna, podstaw UINT.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

na przykład tłumaczy na

`UINT CUIntArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CUIntArray::CUIntArray](../../mfc/reference/cobarray-class.md#cobarray)|Konstruuje pustą tablicę.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CUIntArray:: Add](../../mfc/reference/cobarray-class.md#add)|Dodaje element na końcu tablicy; w razie potrzeby powiększa tablicę.|
|[CUIntArray:: Append](../../mfc/reference/cobarray-class.md#append)|Dołącza kolejną tablicę do tablicy; w razie potrzeby powiększa tablicę.|
|[CUIntArray:: Copy](../../mfc/reference/cobarray-class.md#copy)|Kopiuje kolejną tablicę do tablicy; w razie potrzeby powiększa tablicę.|
|[CUIntArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Zwraca tymczasowe odwołanie do wskaźnika elementu w tablicy.|
|[CUIntArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Zwalnia wszystkie nieużywane pamięci powyżej bieżącej górnej granicy.|
|[CUIntArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Zwraca wartość w danym indeksie.|
|[CUIntArray:: GetCount](../../mfc/reference/cobarray-class.md#getcount)|Pobiera liczbę elementów w tej tablicy.|
|[CUIntArray:: GetData](../../mfc/reference/cobarray-class.md#getdata)|Umożliwia dostęp do elementów w tablicy. Może mieć wartość NULL.|
|[CUIntArray:: GetSize](../../mfc/reference/cobarray-class.md#getsize)|Pobiera liczbę elementów w tej tablicy.|
|[CUIntArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Zwraca największy prawidłowy indeks.|
|[CUIntArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Wstawia element (lub wszystkie elementy w innej tablicy) o określonym indeksie.|
|[CUIntArray:: IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Określa, czy tablica jest pusta.|
|[CUIntArray::](../../mfc/reference/cobarray-class.md#removeall)|Usuwa wszystkie elementy z tej tablicy.|
|[CUIntArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Usuwa element z określonym indeksem.|
|[CUIntArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Ustawia wartość dla danego indeksu; Tablica nie może być większa.|
|[CUIntArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Ustawia wartość dla danego indeksu; w razie potrzeby powiększa tablicę.|
|[CUIntArray:: setSize](../../mfc/reference/cobarray-class.md#setsize)|Ustawia liczbę elementów, które mają być zawarte w tej tablicy.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CUIntArray:: operator \[ \]](../../mfc/reference/cobarray-class.md#operator_at)|Ustawia lub pobiera element pod określonym indeksem.|

## <a name="remarks"></a>Uwagi

Liczba całkowita bez znaku (UINT) różni się od słów i doublewords w tym, że rozmiar fizyczny klasy UINT może ulec zmianie w zależności od docelowego środowiska operacyjnego. Element UINT ma taki sam rozmiar jak DoubleWord.

`CUIntArray` obejmuje makro [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic) w celu obsługi dostępu do typu w czasie wykonywania i zatopienia do obiektu [CDumpContext](../../mfc/reference/cdumpcontext-class.md) . Jeśli potrzebujesz zrzutu pojedynczych elementów liczby całkowitej bez znaku, musisz ustawić głębokość kontekstu zrzutu na 1 lub większą. Niepodpisane tablice całkowite nie mogą być serializowane.

> [!NOTE]
>  Przed użyciem tablicy Użyj `SetSize`, aby ustalić jej rozmiar i przydzielić pamięć. Jeśli nie używasz `SetSize`, dodawanie elementów do tablicy powoduje częste ponowną alokację i kopiowanie. Częste ponowne przydzielanie i kopiowanie są niewydajne i mogą fragmentację pamięci.

Aby uzyskać więcej informacji na temat korzystania z `CUIntArray`, zobacz [kolekcje](../../mfc/collections.md)artykułów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CUIntArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll. h

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
