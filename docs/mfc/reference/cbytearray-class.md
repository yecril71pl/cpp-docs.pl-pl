---
title: Klasa CByteArray
ms.date: 11/04/2016
f1_keywords:
- CByteArray
- AFXCOLL/CByteArray
- AFXCOLL/CByteArray::CByteArray
- AFXCOLL/CByteArray::Add
- AFXCOLL/CByteArray::Append
- AFXCOLL/CByteArray::Copy
- AFXCOLL/CByteArray::ElementAt
- AFXCOLL/CByteArray::FreeExtra
- AFXCOLL/CByteArray::GetAt
- AFXCOLL/CByteArray::GetCount
- AFXCOLL/CByteArray::GetData
- AFXCOLL/CByteArray::GetSize
- AFXCOLL/CByteArray::GetUpperBound
- AFXCOLL/CByteArray::InsertAt
- AFXCOLL/CByteArray::IsEmpty
- AFXCOLL/CByteArray::RemoveAll
- AFXCOLL/CByteArray::RemoveAt
- AFXCOLL/CByteArray::SetAt
- AFXCOLL/CByteArray::SetAtGrow
- AFXCOLL/CByteArray::SetSize
helpviewer_keywords:
- CByteArray [MFC], CByteArray
- CByteArray [MFC], Add
- CByteArray [MFC], Append
- CByteArray [MFC], Copy
- CByteArray [MFC], ElementAt
- CByteArray [MFC], FreeExtra
- CByteArray [MFC], GetAt
- CByteArray [MFC], GetCount
- CByteArray [MFC], GetData
- CByteArray [MFC], GetSize
- CByteArray [MFC], GetUpperBound
- CByteArray [MFC], InsertAt
- CByteArray [MFC], IsEmpty
- CByteArray [MFC], RemoveAll
- CByteArray [MFC], RemoveAt
- CByteArray [MFC], SetAt
- CByteArray [MFC], SetAtGrow
- CByteArray [MFC], SetSize
ms.assetid: 53d4a512-657c-4187-9609-e3f5339a78e0
ms.openlocfilehash: 2453e7c040b9101f9c3a3b018e274b16e76ebea7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446352"
---
# <a name="cbytearray-class"></a>Klasa CByteArray

Obsługuje dynamiczne tablice bajtów.

## <a name="syntax"></a>Składnia

```
class CByteArray : public CObject
```

## <a name="members"></a>Elementy członkowskie

Funkcje składowe `CByteArray` są podobne do funkcji składowych klasy [CObArray](../../mfc/reference/cobarray-class.md). W związku z tym podobieństwem można użyć dokumentacji referencyjnej `CObArray` dla specyficznych dla funkcji składowych. Wszędzie tam, gdzie widzisz wskaźnik `CObject` jako parametr funkcji lub wartość zwracana, Zastąp bajt.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

na przykład tłumaczy na

`BYTE CByteArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CByteArray::CByteArray](../../mfc/reference/cobarray-class.md#cobarray)|Konstruuje pustą tablicę.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CByteArray:: Add](../../mfc/reference/cobarray-class.md#add)|Dodaje element na końcu tablicy; w razie potrzeby powiększa tablicę.|
|[CByteArray:: Append](../../mfc/reference/cobarray-class.md#append)|Dołącza kolejną tablicę do tablicy; w razie potrzeby powiększa tablicę.|
|[CByteArray:: Copy](../../mfc/reference/cobarray-class.md#copy)|Kopiuje kolejną tablicę do tablicy; w razie potrzeby powiększa tablicę.|
|[CByteArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Zwraca tymczasowe odwołanie do bajtu w tablicy.|
|[CByteArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Zwalnia wszystkie nieużywane pamięci powyżej bieżącej górnej granicy.|
|[CByteArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Zwraca wartość w danym indeksie.|
|[CByteArray:: GetCount](../../mfc/reference/cobarray-class.md#getcount)|Pobiera liczbę elementów w tej tablicy.|
|[CByteArray:: GetData](../../mfc/reference/cobarray-class.md#getdata)|Umożliwia dostęp do elementów w tablicy. Może mieć wartość NULL.|
|[CByteArray:: GetSize](../../mfc/reference/cobarray-class.md#getsize)|Pobiera liczbę elementów w tej tablicy.|
|[CByteArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Zwraca największy prawidłowy indeks.|
|[CByteArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Wstawia element (lub wszystkie elementy w innej tablicy) o określonym indeksie.|
|[CByteArray:: IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Określa, czy tablica jest pusta.|
|[CByteArray::](../../mfc/reference/cobarray-class.md#removeall)|Usuwa wszystkie elementy z tej tablicy.|
|[CByteArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Usuwa element z określonym indeksem.|
|[CByteArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Ustawia wartość dla danego indeksu; Tablica nie może być większa.|
|[CByteArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Ustawia wartość dla danego indeksu; w razie potrzeby powiększa tablicę.|
|[CByteArray:: setSize](../../mfc/reference/cobarray-class.md#setsize)|Ustawia liczbę elementów, które mają być zawarte w tej tablicy.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CByteArray:: operator \[ \]](../../mfc/reference/cobarray-class.md#operator_at)|Ustawia lub pobiera element pod określonym indeksem.|

## <a name="remarks"></a>Uwagi

`CByteArray` zawiera IMPLEMENT_SERIAL makro do obsługi serializacji i dumpingu jego elementów. Jeśli tablica bajtów jest przechowywana w archiwum, za pomocą operatora przeciążonego wstawiania ( **<<** ) lub funkcji składowej `Serialize`, każdy element jest z kolei serializowany.

> [!NOTE]
>  Przed użyciem tablicy Użyj `SetSize`, aby ustalić jej rozmiar i przydzielić pamięć. Jeśli nie używasz `SetSize`, dodawanie elementów do tablicy powoduje częste ponowną alokację i kopiowanie. Częste ponowne przydzielanie i kopiowanie są niewydajne i mogą fragmentację pamięci.

Jeśli potrzebujesz debugowania danych wyjściowych z poszczególnych elementów w tablicy, musisz ustawić głębokość obiektu `CDumpContext` na 1 lub większą.

Aby uzyskać więcej informacji na temat korzystania z `CByteArray`, zobacz [kolekcje](../../mfc/collections.md)artykułów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CByteArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll. h

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CObArray](../../mfc/reference/cobarray-class.md)
