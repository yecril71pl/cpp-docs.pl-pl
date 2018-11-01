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
ms.openlocfilehash: 8485f13b91c72d12c2084d2714f2acfa6dda7f01
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478758"
---
# <a name="cautovectorptr-class"></a>Klasa CAutoVectorPtr

Ta klasa reprezentuje obiekt inteligentny wskaźnik przy użyciu nowych wektorów i delete — operatory.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

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
|[CAutoVectorPtr::Allocate](#allocate)|Wywołanie tej metody można przydzielić pamięci wymaganej przez tablicę obiektów, do których prowadzą `CAutoVectorPtr`.|
|[CAutoVectorPtr::Attach](#attach)|Wywołaj tę metodę, aby przejąć prawo własności istniejącego wskaźnika.|
|[CAutoVectorPtr::Detach](#detach)|Wywołaj tę metodę, aby zwolnić własność wskaźnika.|
|[CAutoVectorPtr::Free](#free)|Wywołaj tę metodę, aby usunąć obiekt wskazywany przez `CAutoVectorPtr`.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAutoVectorPtr::operator T *](#operator_t__star)|Operator rzutowania.|
|[CAutoVectorPtr::operator =](#operator_eq)|Operator przypisania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAutoVectorPtr::m_p](#m_p)|Zmiennej składowej danych wskaźnika.|

## <a name="remarks"></a>Uwagi

Ta klasa dostarcza metody do tworzenia i zarządzania inteligentny wskaźnik, co pomoże zapewnić ochronę przed przeciekami pamięci przy zwalnianiu zasobów automatycznie, gdy znajduje się poza zakresem. `CAutoVectorPtr` jest podobny do `CAutoPtr`, jedyną różnicą, że `CAutoVectorPtr` używa [nowy wektor&#91; &#93; ](../../standard-library/new-operators.md#op_new_arr) i [usuwanie wektora&#91; &#93; ](../../standard-library/new-operators.md#op_delete_arr) do przydzielają i zwalniają pamięć zamiast C++ **nowe** i **Usuń** operatorów. Zobacz [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) Jeśli klas kolekcji `CAutoVectorPtr` są wymagane.

Zobacz [CAutoPtr](../../atl/reference/cautoptr-class.md) na przykład za pomocą klasa inteligentnego wskaźnika.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="allocate"></a>  CAutoVectorPtr::Allocate

Wywołanie tej metody można przydzielić pamięci wymaganej przez tablicę obiektów, do których prowadzą `CAutoVectorPtr`.

```
bool Allocate(size_t nElements) throw();
```

### <a name="parameters"></a>Parametry

*nElements*<br/>
Liczba elementów w tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pamięć jest pomyślnie przydzielone, wartość false w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

W kompilacjach do debugowania błędu potwierdzenia wystąpi [CAutoVectorPtr::m_p](#m_p) zmiennej składowej pozwala obecnie przejść do istniejącej wartości; oznacza to, że nie jest równa NULL.

##  <a name="attach"></a>  CAutoVectorPtr::Attach

Wywołaj tę metodę, aby przejąć prawo własności istniejącego wskaźnika.

```
void Attach(T* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
`CAutoVectorPtr` Obiekt będzie przejęcie na własność ten wskaźnik.

### <a name="remarks"></a>Uwagi

Gdy `CAutoVectorPtr` obiektu przejmuje na własność wskaźnika, usługa automatycznie usunie wskaźnika i wszystkie przydzielone dane podczas jego wykracza poza zakres. Jeśli [CAutoVectorPtr::Detach](#detach) jest wywoływana, programisty jest ponownie podany odpowiedzialność za zwalnianie dowolne zasoby przydzielane.

W kompilacjach do debugowania błędu potwierdzenia wystąpi [CAutoVectorPtr::m_p](#m_p) zmiennej składowej pozwala obecnie przejść do istniejącej wartości; oznacza to, że nie jest równa NULL.

##  <a name="cautovectorptr"></a>  CAutoVectorPtr::CAutoVectorPtr

Konstruktor.

```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Istniejącego wskaźnika.

### <a name="remarks"></a>Uwagi

`CAutoVectorPtr` Obiekt może być utworzony przy użyciu istniejącego wskaźnika, w którym to przypadku z tym przenosi własność wskaźnika.

##  <a name="dtor"></a>  CAutoVectorPtr:: ~ CAutoVectorPtr

Destruktor.

```
~CAutoVectorPtr() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie zasoby przydzielone. Wywołania [CAutoVectorPtr::Free](#free).

##  <a name="detach"></a>  CAutoVectorPtr::Detach

Wywołaj tę metodę, aby zwolnić własność wskaźnika.

```
T* Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca kopię wskaźnika.

### <a name="remarks"></a>Uwagi

Uwalnia własność wskaźnika, ustawia [CAutoVectorPtr::m_p](#m_p) zmienną członkowską na wartość NULL i zwraca kopię wskaźnika. Po wywołaniu `Detach`, do programisty, aby zwolnić dowolne przydzielany zasobów za pośrednictwem którego `CAutoVectorPtr` obiekt może mieć wcześniej zakładaliśmy odpowiedzialności.

##  <a name="free"></a>  CAutoVectorPtr::Free

Wywołaj tę metodę, aby usunąć obiekt wskazywany przez `CAutoVectorPtr`.

```
void Free() throw();
```

### <a name="remarks"></a>Uwagi

Obiekt wskazywany przez `CAutoVectorPtr` jest zwalniana i [CAutoVectorPtr::m_p](#m_p) zmiennej składowej ma wartość NULL.

##  <a name="m_p"></a>  CAutoVectorPtr::m_p

Zmiennej składowej danych wskaźnika.

```
T* m_p;
```

### <a name="remarks"></a>Uwagi

Ta zmienna członka przechowuje informacje o wskaźnikach.

##  <a name="operator_eq"></a>  CAutoVectorPtr::operator =

Operator przypisania.

```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do **CAutoVectorPtr\< T >**.

### <a name="remarks"></a>Uwagi

Operator przypisania odłącza `CAutoVectorPtr` obiekt z dowolny wskaźnik bieżącego i dołącza nowy wskaźnik *p*, w tym miejscu.

##  <a name="operator_t__star"></a>  CAutoVectorPtr::operator T *

Operator rzutowania.

```
operator T*() const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wskaźnik do typu danych obiektu zdefiniowane w szablonie klasy.

## <a name="see-also"></a>Zobacz też

[Klasa CAutoPtr](../../atl/reference/cautoptr-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
