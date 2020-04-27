---
title: Klasa CAutoPtr
ms.date: 11/04/2016
f1_keywords:
- CAutoPtr
- ATLBASE/ATL::CAutoPtr
- ATLBASE/ATL::CAutoPtr::CAutoPtr
- ATLBASE/ATL::CAutoPtr::Attach
- ATLBASE/ATL::CAutoPtr::Detach
- ATLBASE/ATL::CAutoPtr::Free
- ATLBASE/ATL::CAutoPtr::m_p
helpviewer_keywords:
- CAutoPtr class
ms.assetid: 08988d53-4fb0-4711-bdfc-8ac29c63f410
ms.openlocfilehash: 7f15e16b075b9a5327723a7f081100313f14ea77
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167724"
---
# <a name="cautoptr-class"></a>Klasa CAutoPtr

Ta klasa reprezentuje obiekt inteligentnego wskaźnika.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```cpp
template <typename T>
class CAutoPtr
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ wskaźnika.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAutoPtr:: CAutoPtr](#cautoptr)|Konstruktor.|
|[CAutoPtr:: ~ CAutoPtr](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAutoPtr:: Attach](#attach)|Wywołaj tę metodę, aby przejąć na własność istniejący wskaźnik.|
|[CAutoPtr::D etach](#detach)|Wywołaj tę metodę, aby zwolnić własność wskaźnika.|
|[CAutoPtr:: Free](#free)|Wywołaj tę metodę, aby usunąć obiekt wskazywany przez `CAutoPtr`.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAutoPtr:: operator T *](#operator_t_star)|Operator rzutowania.|
|[CAutoPtr:: operator =](#operator_eq)|Operator przypisania.|
|[CAutoPtr:: operator->](#operator_ptr)|Operator wskaźnika do składowej.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAutoPtr:: m_p](#m_p)|Zmienna elementu członkowskiego danych wskaźnika.|

## <a name="remarks"></a>Uwagi

Ta klasa zapewnia metody tworzenia inteligentnego wskaźnika i zarządzania nim, co pomoże chronić przed wyciekami pamięci przez Automatyczne zwalnianie zasobów, gdy wykracza poza zakres.

Dodatkowo, `CAutoPtr`Konstruktor kopiujący i operator przypisania przenoszą własność wskaźnika, kopiując wskaźnik źródła do wskaźnika docelowego i ustawiając wskaźnik źródła na wartość null. Z tego względu nie można mieć `CAutoPtr` dwóch obiektów, które przechowują ten sam wskaźnik, co zmniejsza możliwość usunięcia tego samego wskaźnika dwa razy.

`CAutoPtr`upraszcza także tworzenie kolekcji wskaźników. Zamiast wyprowadzania klasy kolekcji i zastępowania destruktora, łatwiej jest utworzyć kolekcję `CAutoPtr` obiektów. Po usunięciu kolekcji `CAutoPtr` obiekty wykraczają poza zakres i automatycznie usuwają siebie.

[CHeapPtr](../../atl/reference/cheapptr-class.md) i warianty działają w taki sam sposób `CAutoPtr`, jak, z tym wyjątkiem, że przydzielają i zwalniają pamięć przy użyciu różnych funkcji sterty zamiast operatorów **New** i **delete** języka C++. [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md) jest podobny do `CAutoPtr`, jedyną różnicą jest użycie **wektora New []** i **delete Vector []** w celu przydzielenia i zwolnienia pamięci.

Zobacz także [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) i [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) , gdy wymagane są tablice lub listy inteligentnych wskaźników.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]

## <a name="cautoptrattach"></a><a name="attach"></a>CAutoPtr:: Attach

Wywołaj tę metodę, aby przejąć na własność istniejący wskaźnik.

```cpp
void Attach(T* p) throw();
```

### <a name="parameters"></a>Parametry

*St*<br/>
`CAutoPtr` Obiekt przejdzie na własność tego wskaźnika.

### <a name="remarks"></a>Uwagi

Gdy `CAutoPtr` obiekt przejmuje własność wskaźnika, automatycznie usunie wskaźnik i wszystkie przydzieloną dane, gdy wykracza poza zakres. Jeśli [CAutoPtr::D etach](#detach) jest wywoływana, programista ponownie otrzymuje odpowiedzialność za zwolnienie wszelkich przyznanych zasobów.

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli element członkowski danych [CAutoPtr:: m_p](#m_p) aktualnie wskazuje istniejącą wartość; oznacza to, że nie jest równa NULL.

### <a name="example"></a>Przykład

Zobacz przykład w [omówieniu CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrcautoptr"></a><a name="cautoptr"></a>CAutoPtr:: CAutoPtr

Konstruktor.

```cpp
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<>
CAutoPtr(CAutoPtr<T>& p) throw();
```

### <a name="parameters"></a>Parametry

*St*<br/>
Istniejący wskaźnik.

*TSrc*<br/>
Typ zarządzany przez inny `CAutoPtr`, używany do inicjowania bieżącego obiektu.

### <a name="remarks"></a>Uwagi

`CAutoPtr` Obiekt można utworzyć przy użyciu istniejącego wskaźnika, w którym to przypadku przenosi własność wskaźnika.

### <a name="example"></a>Przykład

Zobacz przykład w [omówieniu CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrcautoptr"></a><a name="dtor"></a>CAutoPtr:: ~ CAutoPtr

Destruktor.

```cpp
~CAutoPtr() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzieloną zasoby. Wywołania [CAutoPtr:: Free](#free).

## <a name="cautoptrdetach"></a><a name="detach"></a>CAutoPtr::D etach

Wywołaj tę metodę, aby zwolnić własność wskaźnika.

```cpp
T* Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca kopię wskaźnika.

### <a name="remarks"></a>Uwagi

Zwalnia własność wskaźnika, ustawia zmienną składową danych [CAutoPtr:: m_p](#m_p) na null i zwraca kopię wskaźnika. Po wywołaniu `Detach`, programista może zwolnić wszystkie przydzieloną zasoby, do których `CAutoPtr` obiekt mógł wcześniej przyjąć reponsibility.

### <a name="example"></a>Przykład

Zobacz przykład w [omówieniu CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrfree"></a><a name="free"></a>CAutoPtr:: Free

Wywołaj tę metodę, aby usunąć obiekt wskazywany przez `CAutoPtr`.

```cpp
void Free() throw();
```

### <a name="remarks"></a>Uwagi

Obiekt wskazywany przez `CAutoPtr` jest zwolniony, a zmienna elementu członkowskiego danych [CAutoPtr:: m_p](#m_p) ma wartość null.

## <a name="cautoptrm_p"></a><a name="m_p"></a>CAutoPtr:: m_p

Zmienna elementu członkowskiego danych wskaźnika.

```cpp
T* m_p;
```

### <a name="remarks"></a>Uwagi

Ta zmienna członkowska zawiera informacje o wskaźniku.

## <a name="cautoptroperator-"></a><a name="operator_eq"></a>CAutoPtr:: operator =

Operator przypisania.

```cpp
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```

### <a name="parameters"></a>Parametry

*St*<br/>
Wskaźnik.

*TSrc*<br/>
Typ klasy.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do **\< CAutoPtr >T **.

### <a name="remarks"></a>Uwagi

Operator przypisania odłącza `CAutoPtr` obiekt od dowolnego bieżącego wskaźnika i dołącza nowy wskaźnik, *p*, w swoim miejscu.

### <a name="example"></a>Przykład

Zobacz przykład w [omówieniu CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptroperator--gt"></a><a name="operator_ptr"></a>CAutoPtr:: operator-&gt;

Operator wskaźnika do składowej.

```cpp
T* operator->() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość zmiennej składowej danych [CAutoPtr:: m_p](#m_p) .

### <a name="remarks"></a>Uwagi

Użyj tego operatora, aby wywołać metodę w klasie wskazywanej przez `CAutoPtr` obiekt. W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli `CAutoPtr` punkty mają wartość null.

### <a name="example"></a>Przykład

Zobacz przykład w [omówieniu CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptroperator-t"></a><a name="operator_t_star"></a>CAutoPtr:: operator T *

Operator rzutowania.

```cpp
operator T* () const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do typu danych obiektu zdefiniowanego w szablonie klasy.

### <a name="example"></a>Przykład

Zobacz przykład w [omówieniu CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="see-also"></a>Zobacz także

[Klasa CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Klasa CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
