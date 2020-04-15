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
ms.openlocfilehash: e009ca3e3612d10d9cdf62d4bea32224f7b7522c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373997"
---
# <a name="cdwordarray-class"></a>Klasa CDWordArray

Obsługuje tablice 32-bitowych dwusłownych.

## <a name="syntax"></a>Składnia

```
class CDWordArray : public CObject
```

## <a name="members"></a>Elementy członkowskie

Funkcje członkowskie `CDWordArray` są podobne do funkcji członkowskich klasy [CObArray](../../mfc/reference/cobarray-class.md). Ze względu na to podobieństwo `CObArray` można użyć dokumentacji referencyjnej dla specyfiki funkcji elementu członkowskiego. Wszędzie tam, `CObject` gdzie wskaźnik jest widoczny jako `DWORD`parametr funkcji lub zwracana wartość, zastąp .

`CObject* CObArray::GetAt( int <nIndex> ) const;`

na przykład przekłada się na

`DWORD CDWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDWordArray::CDWordArray](../../mfc/reference/cobarray-class.md#cobarray)|Konstruuje pustą tablicę.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDWordArray::Dodaj](../../mfc/reference/cobarray-class.md#add)|Dodaje element na końcu tablicy; w razie potrzeby zwiększa tablicę.|
|[CDWordArray::Dołącz](../../mfc/reference/cobarray-class.md#append)|Dołącza inną tablicę do tablicy; w razie potrzeby zwiększa tablicę.|
|[CDWordArray::Kopiowanie](../../mfc/reference/cobarray-class.md#copy)|Kopiuje inną tablicę do tablicy; w razie potrzeby zwiększa tablicę.|
|[CDWordArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Zwraca tymczasowe odwołanie do bajtu w tablicy.|
|[CDWordArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Zwalnia całą nieużytą pamięć powyżej bieżącej górnej granicy.|
|[CDWordArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Zwraca wartość w danym indeksie.|
|[CDWordArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Pobiera liczbę elementów w tej tablicy.|
|[CDWordArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Umożliwia dostęp do elementów w tablicy. Może mieć wartość NULL.|
|[CDWordArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Pobiera liczbę elementów w tej tablicy.|
|[CDWordArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Zwraca największy prawidłowy indeks.|
|[CDWordArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Wstawia element (lub wszystkie elementy w innej tablicy) w określonym indeksie.|
|[CDWordArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Określa, czy tablica jest pusta.|
|[CDWordArray::UsuńWszystki](../../mfc/reference/cobarray-class.md#removeall)|Usuwa wszystkie elementy z tej tablicy.|
|[CDWordArray::Usuń](../../mfc/reference/cobarray-class.md#removeat)|Usuwa element w określonym indeksie.|
|[CDWordArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Ustawia wartość dla danego indeksu; tablicy nie może rosnąć.|
|[CDWordArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Ustawia wartość dla danego indeksu; w razie potrzeby zwiększa tablicę.|
|[CDWordArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Ustawia liczbę elementów, które mają być zawarte w tej tablicy.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDWordArray::operator \[\]](../../mfc/reference/cobarray-class.md#operator_at)|Ustawia lub pobiera element w określonym indeksie.|

## <a name="remarks"></a>Uwagi

`CDWordArray`zawiera makro `IMPLEMENT_SERIAL` w celu wspierania serializacji i dumpingu jego elementów. Jeśli tablica doublewords jest przechowywana w archiwum, albo z **<<** przeciążonym `Serialize` wstawiania ( ) operatora lub z funkcją elementu członkowskiego, każdy element jest z kolei serializowane.

> [!NOTE]
> Przed użyciem tablicy należy użyć `SetSize` do ustalenia jego rozmiaru i przydzielić dla niej pamięć. Jeśli nie używasz `SetSize`, dodawanie elementów do tablicy powoduje, że często są ponownie przydzielane i kopiowane. Częste ponowne przydzielanie i kopiowanie są nieefektywne i mogą fragmentować pamięć.

Jeśli potrzebujesz danych wyjściowych debugowania z poszczególnych elementów `CDumpContext` w tablicy, należy ustawić głębokość obiektu na 1 lub większą.

Aby uzyskać więcej `CDWordArray`informacji na temat korzystania z programu , zobacz artykuł [Kolekcje](../../mfc/collections.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll.h

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CObArray](../../mfc/reference/cobarray-class.md)
