---
title: Klasa CDWordArray
ms.date: 11/04/2016
f1_keywords:
- CDWordArray
- AFXCOLL/CDWordArray
- AFXCOLL/CDWordArray::CDWordArray
- AFXCOLL/CDWordArray::Add
- AFXCOLL/CDWordArray::Append
- AFXCOLL/CDWordArray::Copy
- AFXCOLL/CDWordArray::ElementAt
- AFXCOLL/CDWordArray::FreeExtra
- AFXCOLL/CDWordArray::GetAt
- AFXCOLL/CDWordArray::GetCount
- AFXCOLL/CDWordArray::GetData
- AFXCOLL/CDWordArray::GetSize
- AFXCOLL/CDWordArray::GetUpperBound
- AFXCOLL/CDWordArray::InsertAt
- AFXCOLL/CDWordArray::IsEmpty
- AFXCOLL/CDWordArray::RemoveAll
- AFXCOLL/CDWordArray::RemoveAt
- AFXCOLL/CDWordArray::SetAt
- AFXCOLL/CDWordArray::SetAtGrow
- AFXCOLL/CDWordArray::SetSize
helpviewer_keywords:
- CDWordArray [MFC], CDWordArray
- CDWordArray [MFC], Add
- CDWordArray [MFC], Append
- CDWordArray [MFC], Copy
- CDWordArray [MFC], ElementAt
- CDWordArray [MFC], FreeExtra
- CDWordArray [MFC], GetAt
- CDWordArray [MFC], GetCount
- CDWordArray [MFC], GetData
- CDWordArray [MFC], GetSize
- CDWordArray [MFC], GetUpperBound
- CDWordArray [MFC], InsertAt
- CDWordArray [MFC], IsEmpty
- CDWordArray [MFC], RemoveAll
- CDWordArray [MFC], RemoveAt
- CDWordArray [MFC], SetAt
- CDWordArray [MFC], SetAtGrow
- CDWordArray [MFC], SetSize
ms.assetid: 581be11e-ced6-47d1-8679-e0b8e7d99494
ms.openlocfilehash: f17caafd01bb5ddfa49afe378bfd79652149ebd8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447346"
---
# <a name="cdwordarray-class"></a>Klasa CDWordArray

Obsługuje tablice 32-bitowe doublewords.

## <a name="syntax"></a>Składnia

```
class CDWordArray : public CObject
```

## <a name="members"></a>Elementy członkowskie

Funkcje składowe `CDWordArray` są podobne do funkcji składowych klasy [CObArray](../../mfc/reference/cobarray-class.md). W związku z tym podobieństwem można użyć dokumentacji referencyjnej `CObArray` dla specyficznych dla funkcji składowych. W każdym przypadku, gdy widzisz wskaźnik `CObject` jako parametr funkcji lub wartość zwracana, Zastąp `DWORD`.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

na przykład tłumaczy na

`DWORD CDWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CDWordArray::CDWordArray](../../mfc/reference/cobarray-class.md#cobarray)|Konstruuje pustą tablicę.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CDWordArray:: Add](../../mfc/reference/cobarray-class.md#add)|Dodaje element na końcu tablicy; w razie potrzeby powiększa tablicę.|
|[CDWordArray:: Append](../../mfc/reference/cobarray-class.md#append)|Dołącza kolejną tablicę do tablicy; w razie potrzeby powiększa tablicę.|
|[CDWordArray:: Copy](../../mfc/reference/cobarray-class.md#copy)|Kopiuje kolejną tablicę do tablicy; w razie potrzeby powiększa tablicę.|
|[CDWordArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Zwraca tymczasowe odwołanie do bajtu w tablicy.|
|[CDWordArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Zwalnia wszystkie nieużywane pamięci powyżej bieżącej górnej granicy.|
|[CDWordArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Zwraca wartość w danym indeksie.|
|[CDWordArray:: GetCount](../../mfc/reference/cobarray-class.md#getcount)|Pobiera liczbę elementów w tej tablicy.|
|[CDWordArray:: GetData](../../mfc/reference/cobarray-class.md#getdata)|Umożliwia dostęp do elementów w tablicy. Może mieć wartość NULL.|
|[CDWordArray:: GetSize](../../mfc/reference/cobarray-class.md#getsize)|Pobiera liczbę elementów w tej tablicy.|
|[CDWordArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Zwraca największy prawidłowy indeks.|
|[CDWordArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Wstawia element (lub wszystkie elementy w innej tablicy) o określonym indeksie.|
|[CDWordArray:: IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Określa, czy tablica jest pusta.|
|[CDWordArray::](../../mfc/reference/cobarray-class.md#removeall)|Usuwa wszystkie elementy z tej tablicy.|
|[CDWordArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Usuwa element z określonym indeksem.|
|[CDWordArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Ustawia wartość dla danego indeksu; Tablica nie może być większa.|
|[CDWordArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Ustawia wartość dla danego indeksu; w razie potrzeby powiększa tablicę.|
|[CDWordArray:: setSize](../../mfc/reference/cobarray-class.md#setsize)|Ustawia liczbę elementów, które mają być zawarte w tej tablicy.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CDWordArray:: operator \[ \]](../../mfc/reference/cobarray-class.md#operator_at)|Ustawia lub pobiera element pod określonym indeksem.|

## <a name="remarks"></a>Uwagi

`CDWordArray` zawiera `IMPLEMENT_SERIAL` makro do obsługi serializacji i dumpingu jego elementów. Jeśli tablica doublewords jest przechowywana w archiwum, za pomocą operatora przeciążonego wstawiania ( **<<** ) lub funkcji składowej `Serialize`, każdy element jest z kolei serializowany.

> [!NOTE]
>  Przed użyciem tablicy Użyj `SetSize`, aby ustalić jej rozmiar i przydzielić pamięć. Jeśli nie używasz `SetSize`, dodawanie elementów do tablicy powoduje częste ponowną alokację i kopiowanie. Częste ponowne przydzielanie i kopiowanie są niewydajne i mogą fragmentację pamięci.

Jeśli potrzebujesz debugowania danych wyjściowych z poszczególnych elementów w tablicy, musisz ustawić głębokość obiektu `CDumpContext` na 1 lub większą.

Aby uzyskać więcej informacji na temat korzystania z `CDWordArray`, zobacz [kolekcje](../../mfc/collections.md)artykułów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll. h

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CObArray](../../mfc/reference/cobarray-class.md)
