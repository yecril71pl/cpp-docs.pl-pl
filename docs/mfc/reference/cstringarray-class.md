---
title: Klasa CStringArray
ms.date: 11/04/2016
f1_keywords:
- CStringArray
- AFXCOLL/CStringArray
- AFXCOLL/CStringArray::CStringArray
- AFXCOLL/CStringArray::Add
- AFXCOLL/CStringArray::Append
- AFXCOLL/CStringArray::Copy
- AFXCOLL/CStringArray::ElementAt
- AFXCOLL/CStringArray::FreeExtra
- AFXCOLL/CStringArray::GetAt
- AFXCOLL/CStringArray::GetCount
- AFXCOLL/CStringArray::GetData
- AFXCOLL/CStringArray::GetSize
- AFXCOLL/CStringArray::GetUpperBound
- AFXCOLL/CStringArray::InsertAt
- AFXCOLL/CStringArray::IsEmpty
- AFXCOLL/CStringArray::RemoveAll
- AFXCOLL/CStringArray::RemoveAt
- AFXCOLL/CStringArray::SetAt
- AFXCOLL/CStringArray::SetAtGrow
- AFXCOLL/CStringArray::SetSize
helpviewer_keywords:
- CStringArray [MFC], CStringArray
- CStringArray [MFC], Add
- CStringArray [MFC], Append
- CStringArray [MFC], Copy
- CStringArray [MFC], ElementAt
- CStringArray [MFC], FreeExtra
- CStringArray [MFC], GetAt
- CStringArray [MFC], GetCount
- CStringArray [MFC], GetData
- CStringArray [MFC], GetSize
- CStringArray [MFC], GetUpperBound
- CStringArray [MFC], InsertAt
- CStringArray [MFC], IsEmpty
- CStringArray [MFC], RemoveAll
- CStringArray [MFC], RemoveAt
- CStringArray [MFC], SetAt
- CStringArray [MFC], SetAtGrow
- CStringArray [MFC], SetSize
ms.assetid: 6c637e06-bba8-4c08-b0fc-cf8cb067ce34
ms.openlocfilehash: 96a272cbbb76b399ed7a3db6848ab3f74a615a38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365986"
---
# <a name="cstringarray-class"></a>Klasa CStringArray

Obsługuje tablice obiektów [CString.](../../atl-mfc-shared/using-cstring.md)

## <a name="syntax"></a>Składnia

```
class CStringArray : public CObject
```

## <a name="members"></a>Elementy członkowskie

Funkcje członkowskie `CStringArray` są podobne do funkcji członkowskich klasy [CObArray](../../mfc/reference/cobarray-class.md). Ze względu na to podobieństwo `CObArray` można użyć dokumentacji referencyjnej dla specyfiki funkcji elementu członkowskiego. Wszędzie tam, `CObject` gdzie widzisz wskaźnik jako wartość zwracaną, podstawiaj [obiekt CString](../../atl-mfc-shared/using-cstring.md) (nie wskaźnik [CString).](../../atl-mfc-shared/using-cstring.md) Wszędzie tam, `CObject` gdzie wskaźnik jest widoczny `LPCTSTR`jako parametr funkcji, zastąp .

`CObject* CObArray::GetAt( int <nIndex> ) const;`

na przykład przekłada się na

`CString CStringArray::GetAt( int <nIndex> ) const;`

i

`void SetAt( int <nIndex>, CObject* <newElement> )`

przekłada się na

`void SetAt( int <nIndex>, LPCTSTR <newElement> )`

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStringArray::CStringArray](../../mfc/reference/cobarray-class.md#cobarray)|Konstruuje pustą tablicę.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStringArray::Dodaj](../../mfc/reference/cobarray-class.md#add)|Dodaje element na końcu tablicy; w razie potrzeby zwiększa tablicę.|
|[CStringArray::Dołącz](../../mfc/reference/cobarray-class.md#append)|Dołącza inną tablicę do tablicy; w razie potrzeby zwiększa tablicę.|
|[CStringArray::Kopiowanie](../../mfc/reference/cobarray-class.md#copy)|Kopiuje inną tablicę do tablicy; w razie potrzeby zwiększa tablicę.|
|[CStringArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Zwraca tymczasowe odwołanie do wskaźnika elementu w tablicy.|
|[CStringArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Zwalnia całą nieużytą pamięć powyżej bieżącej górnej granicy.|
|[CStringArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Zwraca wartość w danym indeksie.|
|[CStringArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Pobiera liczbę elementów w tej tablicy.|
|[CStringArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Umożliwia dostęp do elementów w tablicy. Może mieć **wartość NULL**.|
|[CStringArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Pobiera liczbę elementów w tej tablicy.|
|[CStringArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Zwraca największy prawidłowy indeks.|
|[CStringArray::Wstawianie](../../mfc/reference/cobarray-class.md#insertat)|Wstawia element (lub wszystkie elementy w innej tablicy) w określonym indeksie.|
|[CStringArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Określa, czy tablica jest pusta.|
|[CStringArray::UsuńWszystki](../../mfc/reference/cobarray-class.md#removeall)|Usuwa wszystkie elementy z tej tablicy.|
|[CStringArray::Usuń](../../mfc/reference/cobarray-class.md#removeat)|Usuwa element w określonym indeksie.|
|[CStringArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Ustawia wartość dla danego indeksu; tablicy nie może rosnąć.|
|[CStringArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Ustawia wartość dla danego indeksu; w razie potrzeby zwiększa tablicę.|
|[CStringArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Ustawia liczbę elementów, które mają być zawarte w tej tablicy.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStringArray::operator \[\]](../../mfc/reference/cobarray-class.md#operator_at)|Ustawia lub pobiera element w określonym indeksie.|

## <a name="remarks"></a>Uwagi

`CStringArray`zawiera makro IMPLEMENT_SERIAL w celu wspierania serializacji i dumpingu jego elementów. Jeśli tablica `CString` obiektów jest przechowywana w archiwum, za pomocą przeciążonego operatora wstawiania lub funkcji `Serialize` elementu członkowskiego, każdy element jest serializowany po kolei.

> [!NOTE]
> Przed użyciem tablicy należy użyć `SetSize` do ustalenia jego rozmiaru i przydzielić dla niej pamięć. Jeśli nie używasz `SetSize`, dodawanie elementów do tablicy powoduje, że często są ponownie przydzielane i kopiowane. Częste ponowne przydzielanie i kopiowanie są nieefektywne i mogą fragmentować pamięć.

Jeśli potrzebujesz zrzutu poszczególnych elementów ciągu w tablicy, należy ustawić głębokość kontekstu zrzutu na 1 lub większą.

Po `CString` usunięciu tablicy lub po usunięciu jej elementów pamięć ciągów jest zwalniana odpowiednio.

Aby uzyskać więcej `CStringArray`informacji na temat korzystania z programu , zobacz artykuł [Kolekcje](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CStringArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll.h

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
