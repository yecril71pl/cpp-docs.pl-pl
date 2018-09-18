---
title: Klasa CHeapPtr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CHeapPtr
- ATLCORE/ATL::CHeapPtr
- ATLCORE/ATL::CHeapPtr::CHeapPtr
- ATLCORE/ATL::CHeapPtr::Allocate
- ATLCORE/ATL::CHeapPtr::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtr class
ms.assetid: e5c5bfd4-9bf1-4164-8a83-8155fe253454
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ea4fd429395fc78f36d1f9b3244068c737be49a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033982"
---
# <a name="cheapptr-class"></a>Klasa CHeapPtr

Klasa inteligentnego wskaźnika do zarządzania wskaźniki stosu.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template<typename T, class Allocator=CCRTAllocator>
class CHeapPtr : public CHeapPtrBase<T, Allocator>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ obiektu, który ma być przechowywany na stosie.

*Allocator*<br/>
Klasa alokacji pamięci do użycia.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHeapPtr::CHeapPtr](#cheapptr)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHeapPtr::Allocate](#allocate)|Wywołaj tę metodę można przydzielić pamięci na stosie do przechowywania obiektów.|
|[CHeapPtr::Reallocate](#reallocate)|Wywołaj tę metodę w celu ponownego przydzielenia pamięci na stosie.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHeapPtr::operator =](#operator_eq)|Operator przypisania.|

## <a name="remarks"></a>Uwagi

`CHeapPtr` jest tworzony na podstawie [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) i domyślnie używa procedur CRT (w [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)) do przydzielają i zwalniają pamięć. Klasa [CHeapPtrList](../../atl/reference/cheapptrlist-class.md) może służyć do utworzenia listy wskaźników sterty. Zobacz też [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), który używa procedur alokacji pamięci COM.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

`CHeapPtr`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore.h

##  <a name="allocate"></a>  CHeapPtr::Allocate

Wywołaj tę metodę można przydzielić pamięci na stosie do przechowywania obiektów.

```
bool Allocate(size_t nElements = 1) throw();
```

### <a name="parameters"></a>Parametry

*nElements*<br/>
Liczba elementów używane do obliczania ilość pamięci do przydzielenia. Wartość domyślna to 1.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pamięć została pomyślnie przydzielone, wartość false w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Procedury programu przydzielania są używane do zarezerwować wystarczającej ilości pamięci na stosie, aby przechowywać *nElement* obiekty typu zdefiniowanego w konstruktorze.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#77](../../atl/codesnippet/cpp/cheapptr-class_1.cpp)]

##  <a name="cheapptr"></a>  CHeapPtr::CHeapPtr

Konstruktor.

```
CHeapPtr() throw();
explicit CHeapPtr(T* p) throw();
CHeapPtr(CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Istniejącego wskaźnika stosu lub `CHeapPtr`.

### <a name="remarks"></a>Uwagi

Opcjonalnie można utworzyć wskaźnik stosu przy użyciu istniejącego wskaźnika lub `CHeapPtr` obiektu. Jeśli tak, nowe `CHeapPtr` obiektu przyjmuje odpowiedzialność za zarządzanie nowy wskaźnik i zasobami.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#78](../../atl/codesnippet/cpp/cheapptr-class_2.cpp)]

##  <a name="operator_eq"></a>  CHeapPtr::operator =

Operator przypisania.

```
CHeapPtr<T, Allocator>& operator=(
    CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Istniejące `CHeapPtr` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do zaktualizowanego `CHeapPtr`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#80](../../atl/codesnippet/cpp/cheapptr-class_3.cpp)]

##  <a name="reallocate"></a>  CHeapPtr::Reallocate

Wywołaj tę metodę w celu ponownego przydzielenia pamięci na stosie.

```
bool Reallocate(size_t nElements) throw();
```

### <a name="parameters"></a>Parametry

*nElements*<br/>
Nowy numer elementy służące do obliczania ilość pamięci do przydzielenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pamięć została pomyślnie przydzielone, wartość false w przypadku niepowodzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#79](../../atl/codesnippet/cpp/cheapptr-class_4.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)<br/>
[Klasa CCRTAllocator](../../atl/reference/ccrtallocator-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
