---
title: Klasa CHandle | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CHandle
- ATLBASE/ATL::CHandle
- ATLBASE/ATL::CHandle::CHandle
- ATLBASE/ATL::CHandle::Attach
- ATLBASE/ATL::CHandle::Close
- ATLBASE/ATL::CHandle::Detach
- ATLBASE/ATL::CHandle::m_h
dev_langs:
- C++
helpviewer_keywords:
- CHandle class
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4272f5f8c5e19b32b295c1028de7ab30b22684bb
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757292"
---
# <a name="chandle-class"></a>Klasa CHandle

Ta klasa dostarcza metody do tworzenia i używania obiektu uchwyt.

## <a name="syntax"></a>Składnia

```
class CHandle
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHandle::CHandle](#chandle)|Konstruktor.|
|[CHandle:: ~ CHandle](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHandle::Attach](#attach)|Wywołaj tę metodę, aby dołączyć `CHandle` obiektu istniejące dojście.|
|[CHandle::Close](#close)|Wywołaj tę metodę, aby zamknąć `CHandle` obiektu.|
|[CHandle::Detach](#detach)|Wywołanie tej metody można odłączyć uchwyt z `CHandle` obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHandle::operator UCHWYTU](#operator_handle)|Zwraca wartość przechowywanych dojście.|
|[CHandle::operator =](#operator_eq)|Operator przypisania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CHandle::m_h](#m_h)|Zmiennej członkowskiej, która przechowuje dojście.|

## <a name="remarks"></a>Uwagi

A `CHandle` obiekt może być używany w każdym przypadku, gdy jego uchwyt jest wymagana: główną różnicą jest to, że `CHandle` obiekt zostanie automatycznie usunięty.

> [!NOTE]
>  Niektóre funkcje API użyje wartości NULL jako puste lub nieprawidłowe dojście, a inni korzystają INVALID_HANDLE_VALUE. `CHandle` używane tylko o wartości NULL i będzie INVALID_HANDLE_VALUE należy traktować jako rzeczywistych dojście. Wywołanie interfejsu API, która może zwracać INVALID_HANDLE_VALUE zaewidencjonowania dla tej wartości przed wywołaniem [CHandle::Attach](#attach) lub przekazanie jej do `CHandle` konstruktora i zamiast tego Przekaż wartość NULL.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="attach"></a>  CHandle::Attach

Wywołaj tę metodę, aby dołączyć `CHandle` obiektu istniejące dojście.

```
void Attach(HANDLE h) throw();
```

### <a name="parameters"></a>Parametry

*h*  
`CHandle` potrwa własność uchwytu *h*.

### <a name="remarks"></a>Uwagi

Przypisuje `CHandle` obiekt *h* obsługi. W kompilacjach debuguje ATLASSERT zostanie wygenerowany, jeśli *h* ma wartość NULL. Jest wykonywane nie inne sprawdzenie co ważności uchwytu.

##  <a name="chandle"></a>  CHandle::CHandle

Konstruktor.

```
CHandle() throw();
CHandle(CHandle& h) throw();
explicit CHandle(HANDLE h) throw();
```

### <a name="parameters"></a>Parametry

*h*  
Istniejące dojście lub `CHandle`.

### <a name="remarks"></a>Uwagi

Tworzy nową `CHandle` obiektu opcjonalnie przy użyciu istniejących dojścia lub `CHandle` obiektu.

##  <a name="dtor"></a>  CHandle:: ~ CHandle

Destruktor.

```
~CHandle() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia `CHandle` obiektu przez wywołanie metody [CHandle::Close](#close).

##  <a name="close"></a>  CHandle::Close

Wywołaj tę metodę, aby zamknąć `CHandle` obiektu.

```
void Close() throw();
```

### <a name="remarks"></a>Uwagi

Zamyka otwarte dojście. Jeśli uchwyt ma wartość NULL, które będą odpowiadać sytuacji, gdy `Close` została już wywołana, ATLASSERT zostanie wygenerowany w kompilacjach do debugowania.

##  <a name="detach"></a>  CHandle::Detach

Wywołanie tej metody można odłączyć uchwyt z `CHandle` obiektu.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt odłączany.

### <a name="remarks"></a>Uwagi

Zwalnia własność uchwytu.

##  <a name="m_h"></a>  CHandle::m_h

Zmiennej członkowskiej, która przechowuje dojście.

```
HANDLE m_h;
```

##  <a name="operator_eq"></a>  CHandle::operator =

Operator przypisania.

```
CHandle& operator=(CHandle& h) throw();
```

### <a name="parameters"></a>Parametry

*h*  
`CHandle` potrwa własność uchwytu *h*.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do nowego `CHandle` obiektu.

### <a name="remarks"></a>Uwagi

Jeśli `CHandle` obiekt zawiera obecnie uchwyt, zostaną zamknięte. `CHandle` Obiekt przekazywany będzie miał odwołanie uchwyt, wartość NULL. Gwarantuje to, że dwa `CHandle` obiektów nigdy nie będzie zawierać tej samej aktywnej dojście.

##  <a name="operator_handle"></a>  CHandle::operator UCHWYTU

Zwraca wartość przechowywanych dojście.

```  
operator HANDLE() const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość przechowywaną w [CHandle::m_h](#m_h).

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)
