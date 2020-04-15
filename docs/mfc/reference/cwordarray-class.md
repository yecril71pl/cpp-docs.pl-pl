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
ms.openlocfilehash: 9dfb0b674d52b288ebd05bf7574f1ae05e4ed1f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365911"
---
# <a name="cwordarray-class"></a>Klasa CWordArray

Obsługuje tablice słów 16-bitowych.

## <a name="syntax"></a>Składnia

```
class CWordArray : public CObject
```

## <a name="members"></a>Elementy członkowskie

Funkcje członkowskie `CWordArray` są podobne do funkcji członkowskich klasy [CObArray](../../mfc/reference/cobarray-class.md). Ze względu na to podobieństwo `CObArray` można użyć dokumentacji referencyjnej dla specyfiki funkcji elementu członkowskiego. Wszędzie tam, gdzie widzisz wskaźnik [CObject](../../mfc/reference/cobject-class.md) jako parametr funkcji lub zwracaną wartość, zastąp WORD.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

na przykład przekłada się na

`WORD CWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWordArray::CWordArray](../../mfc/reference/cobarray-class.md#cobarray)|Konstruuje pustą tablicę.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWordArray::Dodaj](../../mfc/reference/cobarray-class.md#add)|Dodaje element na końcu tablicy; w razie potrzeby zwiększa tablicę.|
|[CWordArray::Dołącz](../../mfc/reference/cobarray-class.md#append)|Dołącza inną tablicę do tablicy; w razie potrzeby zwiększa tablicę.|
|[CWordArray::Kopiowanie](../../mfc/reference/cobarray-class.md#copy)|Kopiuje inną tablicę do tablicy; w razie potrzeby zwiększa tablicę.|
|[CWordArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Zwraca tymczasowe odwołanie do wskaźnika elementu w tablicy.|
|[CWordArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Zwalnia całą nieużytą pamięć powyżej bieżącej górnej granicy.|
|[CWordArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Zwraca wartość w danym indeksie.|
|[CWordArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Pobiera liczbę elementów w tej tablicy.|
|[CWordArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Umożliwia dostęp do elementów w tablicy. Może mieć wartość NULL.|
|[CWordArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Pobiera liczbę elementów w tej tablicy.|
|[CWordArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Zwraca największy prawidłowy indeks.|
|[CWordArray::Wstawianie](../../mfc/reference/cobarray-class.md#insertat)|Wstawia element (lub wszystkie elementy w innej tablicy) w określonym indeksie.|
|[CWordArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Określa, czy tablica jest pusta.|
|[CWordArray::UsuńWszystki](../../mfc/reference/cobarray-class.md#removeall)|Usuwa wszystkie elementy z tej tablicy.|
|[CWordArray::Usuń](../../mfc/reference/cobarray-class.md#removeat)|Usuwa element w określonym indeksie.|
|[CWordArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Ustawia wartość dla danego indeksu; tablicy nie może rosnąć.|
|[CWordArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Ustawia wartość dla danego indeksu; w razie potrzeby zwiększa tablicę.|
|[CWordArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Ustawia liczbę elementów, które mają być zawarte w tej tablicy.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWordArray::operator &#91;&#93;](../../mfc/reference/cobarray-class.md#operator_at)|Ustawia lub pobiera element w określonym indeksie.|

## <a name="remarks"></a>Uwagi

`CWordArray`zawiera [makro IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) w celu wspierania serializacji i dumpingu jego elementów. Jeśli tablica słów jest przechowywana w archiwum, za pomocą przeciążonego operatora wstawiania lub [cObject::Serialize](../../mfc/reference/cobject-class.md#serialize) funkcji elementu członkowskiego, każdy element jest z kolei serializowane.

> [!NOTE]
> Przed użyciem tablicy należy użyć `SetSize` do ustalenia jego rozmiaru i przydzielić dla niej pamięć. Jeśli nie używasz `SetSize`, dodawanie elementów do tablicy powoduje, że często są ponownie przydzielane i kopiowane. Częste ponowne przydzielanie i kopiowanie są nieefektywne i mogą fragmentować pamięć.

Jeśli potrzebujesz zrzutu poszczególnych elementów w tablicy, należy ustawić głębokość kontekstu zrzutu na 1 lub większą.

Aby uzyskać więcej `CWordArray`informacji na temat korzystania z programu , zobacz artykuł [Kolekcje](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CWordArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll.h

## <a name="see-also"></a>Zobacz też

[MFC Próbki COLLECT](../../overview/visual-cpp-samples.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
