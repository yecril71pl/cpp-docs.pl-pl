---
title: Klasa CHeapPtrBase | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase::AllocateBytes
- ATLCORE/ATL::CHeapPtrBase::Attach
- ATLCORE/ATL::CHeapPtrBase::Detach
- ATLCORE/ATL::CHeapPtrBase::Free
- ATLCORE/ATL::CHeapPtrBase::ReallocateBytes
- ATLCORE/ATL::CHeapPtrBase::m_pData
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtrBase class
ms.assetid: 501ac1b2-fb34-4c72-b7e6-a4f1fc8fda21
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2a6ab9e03a44f48acca9b949193ceec85eb3ef6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063115"
---
# <a name="cheapptrbase-class"></a>Klasa CHeapPtrBase

Ta klasa stanowi podstawę kilka klas wskaźnika inteligentnego sterty.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <class T, class Allocator = CCRTAllocator>
class CHeapPtrBase
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ obiektu, który ma być przechowywany na stosie.

*Allocator*<br/>
Klasa alokacji pamięci do użycia. Domyślnie CRT procedury służą do przydzielają i zwalniają pamięć.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHeapPtrBase:: ~ CHeapPtrBase](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHeapPtrBase::AllocateBytes](#allocatebytes)|Wywołaj tę metodę można przydzielić pamięci.|
|[CHeapPtrBase::Attach](#attach)|Wywołaj tę metodę, aby przejąć prawo własności istniejącego wskaźnika.|
|[CHeapPtrBase::Detach](#detach)|Wywołaj tę metodę, aby zwolnić własność wskaźnika.|
|[CHeapPtrBase::Free](#free)|Wywołaj tę metodę, aby usunąć obiekt wskazywany przez `CHeapPtrBase`.|
|[CHeapPtrBase::ReallocateBytes](#reallocatebytes)|Wywołaj tę metodę w celu ponownego przydzielenia pamięci.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHeapPtrBase::operator T *](#operator_t_star)|Operator rzutowania.|
|[CHeapPtrBase::operator &](#operator_amp)|& — Operator.|
|[CHeapPtrBase::operator ->](#operator_ptr)|Operator wskaźnika do elementu członkowskiego.|  

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CHeapPtrBase::m_pData](#m_pdata)|Zmiennej składowej danych wskaźnika.|

## <a name="remarks"></a>Uwagi

Ta klasa stanowi podstawę kilka klas wskaźnika inteligentnego sterty. Klasy pochodne, na przykład [CHeapPtr](../../atl/reference/cheapptr-class.md) i [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), dodaj ich własnych operatory i konstruktory. Zobacz te klasy Przykłady implementacji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore.h

##  <a name="allocatebytes"></a>  CHeapPtrBase::AllocateBytes

Wywołaj tę metodę można przydzielić pamięci.

```
bool AllocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Liczba bajtów pamięci do przydzielenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pamięć jest pomyślnie przydzielone, wartość false w przeciwnym razie.

### <a name="remarks"></a>Uwagi

W kompilacjach do debugowania błędu potwierdzenia wystąpi [CHeapPtrBase::m_pData](#m_pdata) zmiennej składowej pozwala obecnie przejść do istniejącej wartości; oznacza to, że nie jest równa NULL.

##  <a name="attach"></a>  CHeapPtrBase::Attach

Wywołaj tę metodę, aby przejąć prawo własności istniejącego wskaźnika.

```
void Attach(T* pData) throw();
```

### <a name="parameters"></a>Parametry

*pData*<br/>
`CHeapPtrBase` Obiekt będzie przejęcie na własność ten wskaźnik.

### <a name="remarks"></a>Uwagi

Gdy `CHeapPtrBase` obiektu przejmuje na własność wskaźnika, usługa automatycznie usunie wskaźnika i wszystkie przydzielone dane podczas jego wykracza poza zakres.

W kompilacjach do debugowania błędu potwierdzenia wystąpi [CHeapPtrBase::m_pData](#m_pdata) zmiennej składowej pozwala obecnie przejść do istniejącej wartości; oznacza to, że nie jest równa NULL.

##  <a name="dtor"></a>  CHeapPtrBase:: ~ CHeapPtrBase

Destruktor.

```
~CHeapPtrBase() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby.

##  <a name="detach"></a>  CHeapPtrBase::Detach

Wywołaj tę metodę, aby zwolnić własność wskaźnika.

```
T* Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca kopię wskaźnika.

### <a name="remarks"></a>Uwagi

Uwalnia własność wskaźnika, ustawia [CHeapPtrBase::m_pData](#m_pdata) zmienną członkowską na wartość NULL i zwraca kopię wskaźnika.

##  <a name="free"></a>  CHeapPtrBase::Free

Wywołaj tę metodę, aby usunąć obiekt wskazywany przez `CHeapPtrBase`.

```
void Free() throw();
```

### <a name="remarks"></a>Uwagi

Obiekt wskazywany przez `CHeapPtrBase` jest zwalniana i [CHeapPtrBase::m_pData](#m_pdata) zmiennej składowej ma wartość NULL.

##  <a name="m_pdata"></a>  CHeapPtrBase::m_pData

Zmiennej składowej danych wskaźnika.

```
T* m_pData;
```

### <a name="remarks"></a>Uwagi

Ta zmienna członka przechowuje informacje o wskaźnikach.

##  <a name="operator_amp"></a>  CHeapPtrBase::operator &amp;

& — Operator.

```
T** operator&() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca adres obiektu wskazywanego przez `CHeapPtrBase` obiektu.

##  <a name="operator_ptr"></a>  CHeapPtrBase::operator-&gt;

Operator wskaźnika do elementu członkowskiego.

```
T* operator->() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość [CHeapPtrBase::m_pData](#m_pdata) zmiennej składowej.

### <a name="remarks"></a>Uwagi

Użyj tego operatora do wywołania metody w klasie, do których prowadzą `CHeapPtrBase` obiektu. W kompilacjach do debugowania błędu potwierdzenia wystąpi `CHeapPtrBase` wskazuje na wartość NULL.

##  <a name="operator_t_star"></a>  CHeapPtrBase::operator T *

Operator rzutowania.

```
operator T*() const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca [CHeapPtrBase::m_pData](#m_pdata).

##  <a name="reallocatebytes"></a>  CHeapPtrBase::ReallocateBytes

Wywołaj tę metodę w celu ponownego przydzielenia pamięci.

```
bool ReallocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Nowe ilość pamięci do przydzielenia, w bajtach.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pamięć jest pomyślnie przydzielone, wartość false w przeciwnym razie.

## <a name="see-also"></a>Zobacz też

[Klasa CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Klasa CComHeapPtr](../../atl/reference/ccomheapptr-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
