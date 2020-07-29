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
ms.openlocfilehash: 65d37396b02d2c11c758915b201eef09cf1935b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226649"
---
# <a name="cautovectorptr-class"></a>Klasa CAutoVectorPtr

Ta klasa reprezentuje obiekt inteligentnego wskaźnika przy użyciu operatorów New i DELETE Vector.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

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
|[CAutoVectorPtr:: ~ CAutoVectorPtr](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAutoVectorPtr:: Allocate](#allocate)|Wywołaj tę metodę, aby przydzielić pamięć wymaganą przez tablicę obiektów wskazywanych przez `CAutoVectorPtr` .|
|[CAutoVectorPtr:: Attach](#attach)|Wywołaj tę metodę, aby przejąć na własność istniejący wskaźnik.|
|[CAutoVectorPtr::D etach](#detach)|Wywołaj tę metodę, aby zwolnić własność wskaźnika.|
|[CAutoVectorPtr:: Free](#free)|Wywołaj tę metodę, aby usunąć obiekt wskazywany przez `CAutoVectorPtr` .|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAutoVectorPtr:: operator T *](#operator_t__star)|Operator rzutowania.|
|[CAutoVectorPtr:: operator =](#operator_eq)|Operator przypisania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAutoVectorPtr:: m_p](#m_p)|Zmienna elementu członkowskiego danych wskaźnika.|

## <a name="remarks"></a>Uwagi

Ta klasa zapewnia metody tworzenia inteligentnego wskaźnika i zarządzania nim, co pomoże chronić przed wyciekami pamięci przez Automatyczne zwalnianie zasobów, gdy wykracza poza zakres. `CAutoVectorPtr`jest podobna do `CAutoPtr` , jedyną różnicą, która `CAutoVectorPtr` używa [wektora New&#91;&#93;](../../standard-library/new-operators.md#op_new_arr) i [Vector Delete&#91;&#93;](../../standard-library/new-operators.md#op_delete_arr) do przydzielania i zwalniania pamięci zamiast **`new`** operatorów i C++ **`delete`** . Zobacz [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) , jeśli klasy kolekcji `CAutoVectorPtr` są wymagane.

Zobacz [CAutoPtr](../../atl/reference/cautoptr-class.md) , aby zapoznać się z przykładem użycia klasy wskaźnika inteligentnego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="cautovectorptrallocate"></a><a name="allocate"></a>CAutoVectorPtr:: Allocate

Wywołaj tę metodę, aby przydzielić pamięć wymaganą przez tablicę obiektów wskazywanych przez `CAutoVectorPtr` .

```
bool Allocate(size_t nElements) throw();
```

### <a name="parameters"></a>Parametry

*nElements*<br/>
Liczba elementów w tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pamięć została pomyślnie przypisana, FAŁSZ w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli zmienna członkowska [CAutoVectorPtr:: m_p](#m_p) aktualnie wskazuje istniejącą wartość; oznacza to, że nie jest równa NULL.

## <a name="cautovectorptrattach"></a><a name="attach"></a>CAutoVectorPtr:: Attach

Wywołaj tę metodę, aby przejąć na własność istniejący wskaźnik.

```cpp
void Attach(T* p) throw();
```

### <a name="parameters"></a>Parametry

*St*<br/>
Obiekt przejdzie na `CAutoVectorPtr` własność tego wskaźnika.

### <a name="remarks"></a>Uwagi

Gdy `CAutoVectorPtr` obiekt przejmuje własność wskaźnika, automatycznie usunie wskaźnik i wszystkie przydzieloną dane, gdy wykracza poza zakres. Jeśli [CAutoVectorPtr::D etach](#detach) jest wywoływana, programista ponownie otrzymuje odpowiedzialność za zwolnienie wszelkich przyznanych zasobów.

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli zmienna członkowska [CAutoVectorPtr:: m_p](#m_p) aktualnie wskazuje istniejącą wartość; oznacza to, że nie jest równa NULL.

## <a name="cautovectorptrcautovectorptr"></a><a name="cautovectorptr"></a>CAutoVectorPtr::CAutoVectorPtr

Konstruktor.

```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>Parametry

*St*<br/>
Istniejący wskaźnik.

### <a name="remarks"></a>Uwagi

`CAutoVectorPtr`Obiekt można utworzyć przy użyciu istniejącego wskaźnika, w którym to przypadku przenosi własność wskaźnika.

## <a name="cautovectorptrcautovectorptr"></a><a name="dtor"></a>CAutoVectorPtr:: ~ CAutoVectorPtr

Destruktor.

```
~CAutoVectorPtr() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzieloną zasoby. Wywołania [CAutoVectorPtr:: Free](#free).

## <a name="cautovectorptrdetach"></a><a name="detach"></a>CAutoVectorPtr::D etach

Wywołaj tę metodę, aby zwolnić własność wskaźnika.

```
T* Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca kopię wskaźnika.

### <a name="remarks"></a>Uwagi

Zwalnia własność wskaźnika, ustawia zmienną członkowską [CAutoVectorPtr:: m_p](#m_p) na null i zwraca kopię wskaźnika. Po wywołaniu `Detach` , programista może zwolnić wszystkie przydzieloną zasoby, do których `CAutoVectorPtr` obiekt mógł wcześniej przyjąć odpowiedzialność.

## <a name="cautovectorptrfree"></a><a name="free"></a>CAutoVectorPtr:: Free

Wywołaj tę metodę, aby usunąć obiekt wskazywany przez `CAutoVectorPtr` .

```cpp
void Free() throw();
```

### <a name="remarks"></a>Uwagi

Obiekt wskazywany przez `CAutoVectorPtr` jest zwolniony, a zmienna członkowska [CAutoVectorPtr:: m_p](#m_p) ma wartość null.

## <a name="cautovectorptrm_p"></a><a name="m_p"></a>CAutoVectorPtr:: m_p

Zmienna elementu członkowskiego danych wskaźnika.

```
T* m_p;
```

### <a name="remarks"></a>Uwagi

Ta zmienna członkowska zawiera informacje o wskaźniku.

## <a name="cautovectorptroperator-"></a><a name="operator_eq"></a>CAutoVectorPtr:: operator =

Operator przypisania.

```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>Parametry

*St*<br/>
Wskaźnik.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do elementu **CAutoVectorPtr \< T > **.

### <a name="remarks"></a>Uwagi

Operator przypisania odłącza `CAutoVectorPtr` obiekt od dowolnego bieżącego wskaźnika i dołącza nowy wskaźnik, *p*, w swoim miejscu.

## <a name="cautovectorptroperator-t-"></a><a name="operator_t__star"></a>CAutoVectorPtr:: operator T *

Operator rzutowania.

```
operator T*() const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wskaźnik do typu danych obiektu zdefiniowanego w szablonie klasy.

## <a name="see-also"></a>Zobacz także

[Klasa CAutoPtr](../../atl/reference/cautoptr-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
