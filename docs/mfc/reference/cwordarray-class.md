---
title: Klasa CWordArray
ms.date: 09/07/2019
f1_keywords:
- CWordArray
- AFXCOLL/CWordArray
- AFXCOLL/CWordArray::CWordArray
- AFXCOLL/CWordArray::Add
- AFXCOLL/CWordArray::Append
- AFXCOLL/CWordArray::Copy
- AFXCOLL/CWordArray::ElementAt
- AFXCOLL/CWordArray::FreeExtra
- AFXCOLL/CWordArray::GetAt
- AFXCOLL/CWordArray::GetCount
- AFXCOLL/CWordArray::GetData
- AFXCOLL/CWordArray::GetSize
- AFXCOLL/CWordArray::GetUpperBound
- AFXCOLL/CWordArray::InsertAt
- AFXCOLL/CWordArray::IsEmpty
- AFXCOLL/CWordArray::RemoveAll
- AFXCOLL/CWordArray::RemoveAt
- AFXCOLL/CWordArray::SetAt
- AFXCOLL/CWordArray::SetAtGrow
- AFXCOLL/CWordArray::SetSize
helpviewer_keywords:
- CWordArray [MFC], CWordArray
- CWordArray [MFC], Add
- CWordArray [MFC], Append
- CWordArray [MFC], Copy
- CWordArray [MFC], ElementAt
- CWordArray [MFC], FreeExtra
- CWordArray [MFC], GetAt
- CWordArray [MFC], GetCount
- CWordArray [MFC], GetData
- CWordArray [MFC], GetSize
- CWordArray [MFC], GetUpperBound
- CWordArray [MFC], InsertAt
- CWordArray [MFC], IsEmpty
- CWordArray [MFC], RemoveAll
- CWordArray [MFC], RemoveAt
- CWordArray [MFC], SetAt
- CWordArray [MFC], SetAtGrow
- CWordArray [MFC], SetSize
ms.assetid: 2ba2c194-2c6c-40ff-9db4-e9dbe57e1f57
ms.openlocfilehash: 99484071c81ed6b766d3e4259d9fc88353b27ea3
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446225"
---
# <a name="cwordarray-class"></a>Klasa CWordArray

Obsługuje tablice słów 16-bitowych.

## <a name="syntax"></a>Składnia

```
class CWordArray : public CObject
```

## <a name="members"></a>Elementy członkowskie

Funkcje składowe `CWordArray` są podobne do funkcji składowych klasy [CObArray](../../mfc/reference/cobarray-class.md). W związku z tym podobieństwem można użyć dokumentacji referencyjnej `CObArray` dla specyficznych dla funkcji składowych. Wszędzie tam, gdzie widzisz wskaźnik [CObject](../../mfc/reference/cobject-class.md) jako parametr funkcji lub wartość zwracaną, Zastąp słowo.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

na przykład tłumaczy na

`WORD CWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CWordArray::CWordArray](../../mfc/reference/cobarray-class.md#cobarray)|Konstruuje pustą tablicę.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CWordArray:: Add](../../mfc/reference/cobarray-class.md#add)|Dodaje element na końcu tablicy; w razie potrzeby powiększa tablicę.|
|[CWordArray:: Append](../../mfc/reference/cobarray-class.md#append)|Dołącza kolejną tablicę do tablicy; w razie potrzeby powiększa tablicę.|
|[CWordArray:: Copy](../../mfc/reference/cobarray-class.md#copy)|Kopiuje kolejną tablicę do tablicy; w razie potrzeby powiększa tablicę.|
|[CWordArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Zwraca tymczasowe odwołanie do wskaźnika elementu w tablicy.|
|[CWordArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Zwalnia wszystkie nieużywane pamięci powyżej bieżącej górnej granicy.|
|[CWordArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Zwraca wartość w danym indeksie.|
|[CWordArray:: GetCount](../../mfc/reference/cobarray-class.md#getcount)|Pobiera liczbę elementów w tej tablicy.|
|[CWordArray:: GetData](../../mfc/reference/cobarray-class.md#getdata)|Umożliwia dostęp do elementów w tablicy. Może mieć wartość NULL.|
|[CWordArray:: GetSize](../../mfc/reference/cobarray-class.md#getsize)|Pobiera liczbę elementów w tej tablicy.|
|[CWordArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Zwraca największy prawidłowy indeks.|
|[CWordArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Wstawia element (lub wszystkie elementy w innej tablicy) o określonym indeksie.|
|[CWordArray:: IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Określa, czy tablica jest pusta.|
|[CWordArray::](../../mfc/reference/cobarray-class.md#removeall)|Usuwa wszystkie elementy z tej tablicy.|
|[CWordArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Usuwa element z określonym indeksem.|
|[CWordArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Ustawia wartość dla danego indeksu; Tablica nie może być większa.|
|[CWordArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Ustawia wartość dla danego indeksu; w razie potrzeby powiększa tablicę.|
|[CWordArray:: setSize](../../mfc/reference/cobarray-class.md#setsize)|Ustawia liczbę elementów, które mają być zawarte w tej tablicy.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CWordArray:: operator&#91;&#93;](../../mfc/reference/cobarray-class.md#operator_at)|Ustawia lub pobiera element pod określonym indeksem.|

## <a name="remarks"></a>Uwagi

`CWordArray` zawiera [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) makro do obsługi serializacji i dumpingu jego elementów. Jeśli tablica wyrazów jest przechowywana w archiwum, ze przeciążonym operatorem wstawiania lub z [CObject:: serializować](../../mfc/reference/cobject-class.md#serialize) elementu członkowskiego, każdy element jest z kolei serializowany.

> [!NOTE]
>  Przed użyciem tablicy Użyj `SetSize`, aby ustalić jej rozmiar i przydzielić pamięć. Jeśli nie używasz `SetSize`, dodawanie elementów do tablicy powoduje częste ponowną alokację i kopiowanie. Częste ponowne przydzielanie i kopiowanie są niewydajne i mogą fragmentację pamięci.

Jeśli potrzebujesz zrzutu poszczególnych elementów w tablicy, musisz ustawić głębokość kontekstu zrzutu na 1 lub większą.

Aby uzyskać więcej informacji na temat korzystania z `CWordArray`, zobacz [kolekcje](../../mfc/collections.md)artykułów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CWordArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll. h

## <a name="see-also"></a>Zobacz też

[ZBIERANIE próbek MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
