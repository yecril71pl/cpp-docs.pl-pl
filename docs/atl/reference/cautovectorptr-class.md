---
title: Klasa CAutoVectorPtr
ms.date: 11/04/2016
f1_keywords:
- CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::Allocate
- ATLBASE/ATL::CAutoVectorPtr::Attach
- ATLBASE/ATL::CAutoVectorPtr::Detach
- ATLBASE/ATL::CAutoVectorPtr::Free
- ATLBASE/ATL::CAutoVectorPtr::m_p
helpviewer_keywords:
- CAutoVectorPtr class
ms.assetid: 0030362b-6bc4-4a47-9b5b-3c3899dceab4
ms.openlocfilehash: 573446256aa89423837ebf73176a73f72054911b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318764"
---
# <a name="cautovectorptr-class"></a>Klasa CAutoVectorPtr

Ta klasa reprezentuje obiekt wskaźnik inteligentny przy użyciu operatorów wektorowych i delete.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<typename T>
class CAutoVectorPtr
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ wskaźnika.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|Konstruktor.|
|[CAutoVectorPtr::~CAutoVectorPtr](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAutoVectorPtr::Przydziel](#allocate)|Wywołanie tej metody, aby przydzielić pamięć wymaganą `CAutoVectorPtr`przez tablicę obiektów wskazywania przez .|
|[CAutoVectorPtr::Dołącz](#attach)|Wywołanie tej metody, aby przejąć na własność istniejącego wskaźnika.|
|[CAutoVectorPtr::Detach](#detach)|Wywołanie tej metody, aby zwolnić własność wskaźnika.|
|[CAutoVectorPtr::Za darmo](#free)|Wywołanie tej metody, aby usunąć `CAutoVectorPtr`obiekt wskazywał przez .|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAutoVectorPtr::operator T *](#operator_t__star)|Operator odlewu.|
|[CAutoVectorPtr::operator =](#operator_eq)|Operator przypisania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAutoVectorPtr::m_p](#m_p)|Zmienna elementu członkowskiego danych wskaźnika.|

## <a name="remarks"></a>Uwagi

Ta klasa udostępnia metody tworzenia i zarządzania inteligentny wskaźnik, który pomoże chronić przed przeciekami pamięci przez automatyczne zwalnianie zasobów, gdy wypadnie poza zakres. `CAutoVectorPtr`jest podobny `CAutoPtr`do , jedyną różnicą jest to, `CAutoVectorPtr` że używa [wektora nowego&#91;&#93;](../../standard-library/new-operators.md#op_new_arr) i [wektora delete&#91;&#93;](../../standard-library/new-operators.md#op_delete_arr) przydzielić i zwolnić pamięć zamiast C++ **nowe** i **delete** operatorów. Zobacz [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) jeśli `CAutoVectorPtr` klasy kolekcji są wymagane.

Zobacz [CAutoPtr](../../atl/reference/cautoptr-class.md) na przykład przy użyciu klasy inteligentnego wskaźnika.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="cautovectorptrallocate"></a><a name="allocate"></a>CAutoVectorPtr::Przydziel

Wywołanie tej metody, aby przydzielić pamięć wymaganą `CAutoVectorPtr`przez tablicę obiektów wskazywania przez .

```
bool Allocate(size_t nElements) throw();
```

### <a name="parameters"></a>Parametry

*nElementy*<br/>
Liczba elementów w tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli pamięć została pomyślnie przydzielona, false na niepowodzenie.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli zmienna elementu członkowskiego [CAutoVectorPtr::m_p](#m_p) aktualnie wskazuje na istniejącą wartość; oznacza to, że nie jest równa NULL.

## <a name="cautovectorptrattach"></a><a name="attach"></a>CAutoVectorPtr::Dołącz

Wywołanie tej metody, aby przejąć na własność istniejącego wskaźnika.

```
void Attach(T* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Obiekt `CAutoVectorPtr` przejmie na własność ten wskaźnik.

### <a name="remarks"></a>Uwagi

Gdy `CAutoVectorPtr` obiekt przejmuje na własność wskaźnik, automatycznie usunie wskaźnik i wszystkie przydzielone dane, gdy wyjdzie poza zakres. Jeśli [CAutoVectorPtr::Detach](#detach) jest wywoływana, programista jest ponownie odpowiedzialny za zwalnianie wszelkich przydzielonych zasobów.

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli zmienna elementu członkowskiego [CAutoVectorPtr::m_p](#m_p) aktualnie wskazuje na istniejącą wartość; oznacza to, że nie jest równa NULL.

## <a name="cautovectorptrcautovectorptr"></a><a name="cautovectorptr"></a>CAutoVectorPtr::CAutoVectorPtr

Konstruktor.

```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Istniejący wskaźnik.

### <a name="remarks"></a>Uwagi

Obiekt `CAutoVectorPtr` można utworzyć za pomocą istniejącego wskaźnika, w którym to przypadku przenosi własność wskaźnika.

## <a name="cautovectorptrcautovectorptr"></a><a name="dtor"></a>CAutoVectorPtr::~CAutoVectorPtr

Destruktor.

```
~CAutoVectorPtr() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby. Wywołuje [CAutoVectorPtr::Free](#free).

## <a name="cautovectorptrdetach"></a><a name="detach"></a>CAutoVectorPtr::Detach

Wywołanie tej metody, aby zwolnić własność wskaźnika.

```
T* Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca kopię wskaźnika.

### <a name="remarks"></a>Uwagi

Zwalnia własność [wskaźnika, ustawia zmienną CAutoVectorPtr::m_p](#m_p) zmienną elementu członkowskiego na NULL i zwraca kopię wskaźnika. Po `Detach`wywołaniu program programista musi zwolnić wszystkie przydzielone `CAutoVectorPtr` zasoby, za które obiekt mógł wcześniej przejąć odpowiedzialność.

## <a name="cautovectorptrfree"></a><a name="free"></a>CAutoVectorPtr::Za darmo

Wywołanie tej metody, aby usunąć `CAutoVectorPtr`obiekt wskazywał przez .

```
void Free() throw();
```

### <a name="remarks"></a>Uwagi

Obiekt wskazany przez `CAutoVectorPtr` jest zwolniona, a zmienna elementu członkowskiego [CAutoVectorPtr::m_p](#m_p) jest ustawiona na wartość NULL.

## <a name="cautovectorptrm_p"></a><a name="m_p"></a>CAutoVectorPtr::m_p

Zmienna elementu członkowskiego danych wskaźnika.

```
T* m_p;
```

### <a name="remarks"></a>Uwagi

Ta zmienna elementu członkowskiego zawiera informacje o wskaźniku.

## <a name="cautovectorptroperator-"></a><a name="operator_eq"></a>CAutoVectorPtr::operator =

Operator przypisania.

```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Wskaźnik.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do **>\< CAutoVectorPtr T **.

### <a name="remarks"></a>Uwagi

Operator przypisania odłącza obiekt od bieżącego `CAutoVectorPtr` wskaźnika i dołącza nowy wskaźnik , *p*, w jego miejsce.

## <a name="cautovectorptroperator-t-"></a><a name="operator_t__star"></a>CAutoVectorPtr::operator T *

Operator odlewu.

```
operator T*() const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wskaźnik do typu danych obiektu zdefiniowanego w szablonie klasy.

## <a name="see-also"></a>Zobacz też

[Klasa CAutoPtr](../../atl/reference/cautoptr-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
