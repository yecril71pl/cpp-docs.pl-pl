---
title: Klasa CHandle
ms.date: 07/09/2019
f1_keywords:
- CHandle
- ATLBASE/ATL::CHandle
- ATLBASE/ATL::CHandle::CHandle
- ATLBASE/ATL::CHandle::Attach
- ATLBASE/ATL::CHandle::Close
- ATLBASE/ATL::CHandle::Detach
- ATLBASE/ATL::CHandle::m_h
helpviewer_keywords:
- CHandle class
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
ms.openlocfilehash: 4b883bdf3159c40f8d74866f04f655ae73d82a8a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747698"
---
# <a name="chandle-class"></a>Klasa CHandle

Ta klasa zawiera metody tworzenia i używania obiektu dojścia.

## <a name="syntax"></a>Składnia

```
class CHandle
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHandle::CHandle](#chandle)|Konstruktor.|
|[CHandle::~CHandle](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHandle::Dołącz](#attach)|Wywołanie tej metody, aby dołączyć `CHandle` obiekt do istniejącego dojścia.|
|[CHandle::Zamknij](#close)|Wywołanie tej metody, aby zamknąć `CHandle` obiekt.|
|[CHandle::Detach](#detach)|Wywołanie tej metody, aby `CHandle` odłączyć dojście od obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHandle::operator HANDLE](#operator_handle)|Zwraca wartość przechowywanego dojścia.|
|[CHandle::operator =](#operator_eq)|Operator przypisania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CHandle::m_h](#m_h)|Zmienna elementu członkowskiego, która przechowuje dojście.|

## <a name="remarks"></a>Uwagi

Obiekt `CHandle` może być używany za każdym razem, gdy wymagany `CHandle` jest dojście: główną różnicą jest to, że obiekt zostanie automatycznie usunięty.

> [!NOTE]
> Niektóre funkcje interfejsu API będą używać null jako pustego lub nieprawidłowego uchwytu, podczas gdy inne używają INVALID_HANDLE_VALUE. `CHandle`używa tylko NULL i będzie traktować INVALID_HANDLE_VALUE jako prawdziwy uchwyt. Jeśli wywołasz interfejs API, który może zwrócić INVALID_HANDLE_VALUE, należy sprawdzić tę wartość przed wywołaniem `CHandle` [CHandle::Attach](#attach) lub przekazywania go do konstruktora i zamiast tego przekazać NULL.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="chandleattach"></a><a name="attach"></a>CHandle::Dołącz

Wywołanie tej metody, aby dołączyć `CHandle` obiekt do istniejącego dojścia.

```cpp
void Attach(HANDLE h) throw();
```

### <a name="parameters"></a>Parametry

*H*<br/>
`CHandle`przejmie na własność uchwyt *h*.

### <a name="remarks"></a>Uwagi

Przypisuje `CHandle` obiekt do uchwytu *h,* a następnie wywołuje **h.Detach()**. W kompilacjach debugowania ATLASSERT zostanie podniesiony, jeśli *h* jest NULL. Nie ma innego sprawdzenia ważności uchwytu.

## <a name="chandlechandle"></a><a name="chandle"></a>CHandle::CHandle

Konstruktor.

```
CHandle() throw();
CHandle(CHandle& h) throw();
explicit CHandle(HANDLE h) throw();
```

### <a name="parameters"></a>Parametry

*H*<br/>
Istniejący uchwyt `CHandle`lub .

### <a name="remarks"></a>Uwagi

Tworzy nowy `CHandle` obiekt, opcjonalnie przy `CHandle` użyciu istniejącego uchwytu lub obiektu.

## <a name="chandlechandle"></a><a name="dtor"></a>CHandle::~CHandle

Destruktor.

```
~CHandle() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia obiekt, `CHandle` wywołując [CHandle::Close](#close).

## <a name="chandleclose"></a><a name="close"></a>CHandle::Zamknij

Wywołanie tej metody, aby zamknąć `CHandle` obiekt.

```cpp
void Close() throw();
```

### <a name="remarks"></a>Uwagi

Zamyka uchwyt otwartego obiektu. Jeśli dojście jest NULL, co `Close` będzie w przypadku, jeśli został już wywołany, ATLASSERT zostaną podniesione w debugowania kompilacji.

## <a name="chandledetach"></a><a name="detach"></a>CHandle::Detach

Wywołanie tej metody, aby `CHandle` odłączyć dojście od obiektu.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca odłączony uchwyt.

### <a name="remarks"></a>Uwagi

Zwalnia własność dojścia.

## <a name="chandlem_h"></a><a name="m_h"></a>CHandle::m_h

Zmienna elementu członkowskiego, która przechowuje dojście.

```
HANDLE m_h;
```

## <a name="chandleoperator-"></a><a name="operator_eq"></a>CHandle::operator =

Operator przypisania.

```
CHandle& operator=(CHandle& h) throw();
```

### <a name="parameters"></a>Parametry

*H*<br/>
`CHandle`przejmie na własność uchwyt *h*.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do `CHandle` nowego obiektu.

### <a name="remarks"></a>Uwagi

Jeśli `CHandle` obiekt obecnie zawiera dojście, zostanie zamknięty. Obiekt `CHandle` przekazywany w będzie miał jego odwołanie do dojścia ustawionego na NULL. Gwarantuje to, `CHandle` że dwa obiekty nigdy nie będzie zawierać tego samego aktywnego uchwytu.

## <a name="chandleoperator-handle"></a><a name="operator_handle"></a>CHandle::operator HANDLE

Zwraca wartość przechowywanego dojścia.

```
operator HANDLE() const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość przechowywaną w [CHandle::m_h](#m_h).

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
