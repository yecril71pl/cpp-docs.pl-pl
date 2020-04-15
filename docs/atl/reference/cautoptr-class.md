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
ms.openlocfilehash: cb8e3d6b71db6ab60b3b246bd8c5bf4f2c9aaa34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321254"
---
# <a name="cautoptr-class"></a>Klasa CAutoPtr

Ta klasa reprezentuje obiekt wskaźnika inteligentnego.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <typename T>
class CAutoPtr
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ wskaźnika.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAutoPtr::CAutoPtr](#cautoptr)|Konstruktor.|
|[CAutoPtr::~CAutoPtr](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAutoPtr::Dołącz](#attach)|Wywołanie tej metody, aby przejąć na własność istniejącego wskaźnika.|
|[CAutoPtr::Detach](#detach)|Wywołanie tej metody, aby zwolnić własność wskaźnika.|
|[CAutoPtr::Za darmo](#free)|Wywołanie tej metody, aby usunąć `CAutoPtr`obiekt wskazywał przez .|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAutoPtr::operator T*](#operator_t_star)|Operator odlewu.|
|[CAutoPtr::operator =](#operator_eq)|Operator przypisania.|
|[CAutoPtr::operator ->](#operator_ptr)|Operator wskaźnik-element.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAutoPtr::m_p](#m_p)|Zmienna elementu członkowskiego danych wskaźnika.|

## <a name="remarks"></a>Uwagi

Ta klasa udostępnia metody tworzenia i zarządzania inteligentny wskaźnik, który pomoże chronić przed przeciekami pamięci przez automatyczne zwalnianie zasobów, gdy wypadnie poza zakres.

`CAutoPtr`Ponadto konstruktor kopiowania i przypisania operator transferu własności wskaźnika, kopiowanie wskaźnika źródłowego do wskaźnika docelowego i ustawienie wskaźnika źródłowego do NULL. W związku z tym `CAutoPtr` jest niemożliwe, aby mieć dwa obiekty, z których każdy przechowuje ten sam wskaźnik, a to zmniejsza możliwość usuwania tego samego wskaźnika dwa razy.

`CAutoPtr`upraszcza również tworzenie kolekcji wskaźników. Zamiast wyprowadzania klasy kolekcji i zastępowania destruktora, jest prostsze `CAutoPtr` do tworzenia kolekcji obiektów. Po usunięciu kolekcji `CAutoPtr` obiekty wyjdą poza zakres i automatycznie usunie się.

[CHeapPtr](../../atl/reference/cheapptr-class.md) i warianty działają w `CAutoPtr`taki sam sposób jak , z tą różnicą, że przydzielają i zwalniają pamięć przy użyciu różnych funkcji sterty zamiast **operatorów C++ new** i **delete.** [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md) jest `CAutoPtr`podobny do , jedyną różnicą jest to, że używa **wektora new[]** i **wektor delete[]** do przydzielenia i wolnej pamięci.

Zobacz też [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) i [CAutoPtrList,](../../atl/reference/cautoptrlist-class.md) gdy wymagane są tablice lub listy inteligentnych wskaźników.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]

## <a name="cautoptrattach"></a><a name="attach"></a>CAutoPtr::Dołącz

Wywołanie tej metody, aby przejąć na własność istniejącego wskaźnika.

```
void Attach(T* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Obiekt `CAutoPtr` przejmie na własność ten wskaźnik.

### <a name="remarks"></a>Uwagi

Gdy `CAutoPtr` obiekt przejmuje na własność wskaźnik, automatycznie usunie wskaźnik i wszystkie przydzielone dane, gdy wyjdzie poza zakres. Jeśli [CAutoPtr::Detach](#detach) jest wywoływana, programista jest ponownie odpowiedzialny za zwalnianie wszelkich przydzielonych zasobów.

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli element członkowski danych [CAutoPtr::m_p](#m_p) aktualnie wskazuje na istniejącą wartość; oznacza to, że nie jest równa NULL.

### <a name="example"></a>Przykład

Zobacz przykład w [przeglądzie CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrcautoptr"></a><a name="cautoptr"></a>CAutoPtr::CAutoPtr

Konstruktor.

```
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<>
CAutoPtr(CAutoPtr<T>& p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Istniejący wskaźnik.

*Tsrc ( TSRC )*<br/>
Typ zarządzany przez `CAutoPtr`inny , używany do inicjowania bieżącego obiektu.

### <a name="remarks"></a>Uwagi

Obiekt `CAutoPtr` można utworzyć za pomocą istniejącego wskaźnika, w którym to przypadku przenosi własność wskaźnika.

### <a name="example"></a>Przykład

Zobacz przykład w [przeglądzie CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrcautoptr"></a><a name="dtor"></a>CAutoPtr::~CAutoPtr

Destruktor.

```
~CAutoPtr() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby. Połączenia [CAutoPtr::Free](#free).

## <a name="cautoptrdetach"></a><a name="detach"></a>CAutoPtr::Detach

Wywołanie tej metody, aby zwolnić własność wskaźnika.

```
T* Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca kopię wskaźnika.

### <a name="remarks"></a>Uwagi

Zwalnia własność wskaźnika, ustawia zmienną elementu członkowskiego [CAutoPtr::m_p](#m_p) na NULL i zwraca kopię wskaźnika. Po `Detach`wywołaniu program programista musi zwolnić przydzielone zasoby, nad którymi `CAutoPtr` obiekt mógł wcześniej przyjąć odpowiedzialność.

### <a name="example"></a>Przykład

Zobacz przykład w [przeglądzie CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrfree"></a><a name="free"></a>CAutoPtr::Za darmo

Wywołanie tej metody, aby usunąć `CAutoPtr`obiekt wskazywał przez .

```
void Free() throw();
```

### <a name="remarks"></a>Uwagi

Obiekt wskazany przez `CAutoPtr` jest zwalniany, a zmienna elementu członkowskiego [CAutoPtr::m_p](#m_p) danych jest ustawiona na wartość NULL.

## <a name="cautoptrm_p"></a><a name="m_p"></a>CAutoPtr::m_p

Zmienna elementu członkowskiego danych wskaźnika.

```
T* m_p;
```

### <a name="remarks"></a>Uwagi

Ta zmienna elementu członkowskiego zawiera informacje o wskaźniku.

## <a name="cautoptroperator-"></a><a name="operator_eq"></a>CAutoPtr::operator =

Operator przypisania.

```
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```

### <a name="parameters"></a>Parametry

*P*<br/>
Wskaźnik.

*Tsrc ( TSRC )*<br/>
Typ klasy.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do **>\< CAutoPtr T **.

### <a name="remarks"></a>Uwagi

Operator przypisania odłącza obiekt od bieżącego `CAutoPtr` wskaźnika i dołącza nowy wskaźnik , *p*, w jego miejsce.

### <a name="example"></a>Przykład

Zobacz przykład w [przeglądzie CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptroperator--gt"></a><a name="operator_ptr"></a>CAutoPtr::operator -&gt;

Operator wskaźnik-element.

```
T* operator->() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość zmiennej elementu członkowskiego [CAutoPtr::m_p](#m_p) danych.

### <a name="remarks"></a>Uwagi

Ten operator służy do wywoływania metody w `CAutoPtr` klasie wskazywaluj przez obiekt. W kompilacjach debugowania błąd potwierdzenia `CAutoPtr` wystąpi, jeśli wskazuje wartość NULL.

### <a name="example"></a>Przykład

Zobacz przykład w [przeglądzie CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptroperator-t"></a><a name="operator_t_star"></a>CAutoPtr::operator T*

Operator odlewu.

```
operator T* () const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do typu danych obiektu zdefiniowanego w szablonie klasy.

### <a name="example"></a>Przykład

Zobacz przykład w [przeglądzie CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="see-also"></a>Zobacz też

[Klasa CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Klasa CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
