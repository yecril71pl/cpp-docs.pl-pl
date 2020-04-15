---
title: Klasa CHeapPtr
ms.date: 11/04/2016
f1_keywords:
- CHeapPtr
- ATLCORE/ATL::CHeapPtr
- ATLCORE/ATL::CHeapPtr::CHeapPtr
- ATLCORE/ATL::CHeapPtr::Allocate
- ATLCORE/ATL::CHeapPtr::Reallocate
helpviewer_keywords:
- CHeapPtr class
ms.assetid: e5c5bfd4-9bf1-4164-8a83-8155fe253454
ms.openlocfilehash: a512aa974cb57072915f887f0c2a20ed1263ffa3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326917"
---
# <a name="cheapptr-class"></a>Klasa CHeapPtr

Klasa inteligentnego wskaźnika do zarządzania wskaźnikami sterty.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<typename T, class Allocator=CCRTAllocator>
class CHeapPtr : public CHeapPtrBase<T, Allocator>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ obiektu, który ma być przechowywany na stercie.

*Programu przydzielania*<br/>
Klasa alokacji pamięci do użycia.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHeapPtr::CHeapPtr](#cheapptr)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHeapPtr::Przydziel](#allocate)|Wywołanie tej metody, aby przydzielić pamięć na stercie do przechowywania obiektów.|
|[CHeapPtr::Ponowne przydzielenie](#reallocate)|Wywołanie tej metody, aby ponownie przydzielić pamięć na stosie.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHeapPtr::operator =](#operator_eq)|Operator przypisania.|

## <a name="remarks"></a>Uwagi

`CHeapPtr`pochodzi z [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) i domyślnie używa procedur CRT (w [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)) do przydzielania i zwalniania pamięci. Klasa [CHeapPtrList](../../atl/reference/cheapptrlist-class.md) może służyć do konstruowania listy wskaźników sterty. Zobacz też [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), który używa procedur alokacji pamięci COM.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cheapptrbase](../../atl/reference/cheapptrbase-class.md)

`CHeapPtr`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore.h

## <a name="cheapptrallocate"></a><a name="allocate"></a>CHeapPtr::Przydziel

Wywołanie tej metody, aby przydzielić pamięć na stercie do przechowywania obiektów.

```
bool Allocate(size_t nElements = 1) throw();
```

### <a name="parameters"></a>Parametry

*nElementy*<br/>
Liczba elementów używanych do obliczania ilości pamięci do przydzielenia. Wartość domyślna to 1.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli pamięć została pomyślnie przydzielona, false na niepowodzenie.

### <a name="remarks"></a>Uwagi

Procedury alokatora są używane do rezerwowania wystarczającej ilości pamięci na stercie do przechowywania *nElement* obiektów typu zdefiniowanego w konstruktorze.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#77](../../atl/codesnippet/cpp/cheapptr-class_1.cpp)]

## <a name="cheapptrcheapptr"></a><a name="cheapptr"></a>CHeapPtr::CHeapPtr

Konstruktor.

```
CHeapPtr() throw();
explicit CHeapPtr(T* p) throw();
CHeapPtr(CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Istniejący wskaźnik sterty lub `CHeapPtr`.

### <a name="remarks"></a>Uwagi

Wskaźnik sterty można opcjonalnie utworzyć przy użyciu `CHeapPtr` istniejącego wskaźnika lub obiektu. Jeśli tak, `CHeapPtr` nowy obiekt przejmuje odpowiedzialność za zarządzanie nowym wskaźnikiem i zasobami.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#78](../../atl/codesnippet/cpp/cheapptr-class_2.cpp)]

## <a name="cheapptroperator-"></a><a name="operator_eq"></a>CHeapPtr::operator =

Operator przypisania.

```
CHeapPtr<T, Allocator>& operator=(
    CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Istniejący `CHeapPtr` obiekt.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do `CHeapPtr`zaktualizowanego .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#80](../../atl/codesnippet/cpp/cheapptr-class_3.cpp)]

## <a name="cheapptrreallocate"></a><a name="reallocate"></a>CHeapPtr::Ponowne przydzielenie

Wywołanie tej metody, aby ponownie przydzielić pamięć na stosie.

```
bool Reallocate(size_t nElements) throw();
```

### <a name="parameters"></a>Parametry

*nElementy*<br/>
Nowa liczba elementów używanych do obliczania ilości pamięci do przydzielenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli pamięć została pomyślnie przydzielona, false na niepowodzenie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#79](../../atl/codesnippet/cpp/cheapptr-class_4.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)<br/>
[Klasa CCRTAllocator](../../atl/reference/ccrtallocator-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
