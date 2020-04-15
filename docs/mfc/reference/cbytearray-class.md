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
ms.openlocfilehash: 9da30f6546a69a51c56bf4b27668e1603c13290b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352386"
---
# <a name="cbytearray-class"></a>Klasa CByteArray

Obsługuje dynamiczne tablice bajtów.

## <a name="syntax"></a>Składnia

```
class CByteArray : public CObject
```

## <a name="members"></a>Elementy członkowskie

Funkcje członkowskie `CByteArray` są podobne do funkcji członkowskich klasy [CObArray](../../mfc/reference/cobarray-class.md). Ze względu na to podobieństwo `CObArray` można użyć dokumentacji referencyjnej dla specyfiki funkcji elementu członkowskiego. Wszędzie tam, `CObject` gdzie widzisz wskaźnik jako parametr funkcji lub zwraca wartość, podstawianie pliku BYTE.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

na przykład przekłada się na

`BYTE CByteArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CByteArray::CByteArray](../../mfc/reference/cobarray-class.md#cobarray)|Konstruuje pustą tablicę.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CByteArray::Dodaj](../../mfc/reference/cobarray-class.md#add)|Dodaje element na końcu tablicy; w razie potrzeby zwiększa tablicę.|
|[CByteArray::Dołącz](../../mfc/reference/cobarray-class.md#append)|Dołącza inną tablicę do tablicy; w razie potrzeby zwiększa tablicę.|
|[CByteArray::Kopiowanie](../../mfc/reference/cobarray-class.md#copy)|Kopiuje inną tablicę do tablicy; w razie potrzeby zwiększa tablicę.|
|[CByteArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Zwraca tymczasowe odwołanie do bajtu w tablicy.|
|[CByteArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Zwalnia całą nieużytą pamięć powyżej bieżącej górnej granicy.|
|[CByteArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Zwraca wartość w danym indeksie.|
|[CByteArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Pobiera liczbę elementów w tej tablicy.|
|[CByteArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Umożliwia dostęp do elementów w tablicy. Może mieć wartość NULL.|
|[CByteArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Pobiera liczbę elementów w tej tablicy.|
|[CByteArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Zwraca największy prawidłowy indeks.|
|[CByteArray::Wstawianie](../../mfc/reference/cobarray-class.md#insertat)|Wstawia element (lub wszystkie elementy w innej tablicy) w określonym indeksie.|
|[CByteArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Określa, czy tablica jest pusta.|
|[CByteArray::UsuńWszystki](../../mfc/reference/cobarray-class.md#removeall)|Usuwa wszystkie elementy z tej tablicy.|
|[CByteArray::Usuń](../../mfc/reference/cobarray-class.md#removeat)|Usuwa element w określonym indeksie.|
|[CByteArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Ustawia wartość dla danego indeksu; tablicy nie może rosnąć.|
|[CByteArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Ustawia wartość dla danego indeksu; w razie potrzeby zwiększa tablicę.|
|[CByteArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Ustawia liczbę elementów, które mają być zawarte w tej tablicy.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CByteArray::operator \[\]](../../mfc/reference/cobarray-class.md#operator_at)|Ustawia lub pobiera element w określonym indeksie.|

## <a name="remarks"></a>Uwagi

`CByteArray`zawiera makro IMPLEMENT_SERIAL w celu wspierania serializacji i dumpingu jego elementów. Jeśli tablica bajtów jest przechowywana w archiwum, za **<<** pomocą przeciążonego operatora wstawiania ( ) lub z funkcją `Serialize` elementu członkowskiego, każdy element jest z kolei serializowany.

> [!NOTE]
> Przed użyciem tablicy należy użyć `SetSize` do ustalenia jego rozmiaru i przydzielić dla niej pamięć. Jeśli nie używasz `SetSize`, dodawanie elementów do tablicy powoduje, że często są ponownie przydzielane i kopiowane. Częste ponowne przydzielanie i kopiowanie są nieefektywne i mogą fragmentować pamięć.

Jeśli potrzebujesz danych wyjściowych debugowania z poszczególnych elementów `CDumpContext` w tablicy, należy ustawić głębokość obiektu na 1 lub większą.

Aby uzyskać więcej `CByteArray`informacji na temat korzystania z programu , zobacz artykuł [Kolekcje](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CByteArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll.h

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CObArray](../../mfc/reference/cobarray-class.md)
