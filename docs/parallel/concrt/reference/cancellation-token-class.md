---
title: cancellation_token — Klasa
ms.date: 11/04/2016
f1_keywords:
- cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::deregister_callback
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_cancelable
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_canceled
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::none
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::register_callback
helpviewer_keywords:
- cancellation_token class
ms.assetid: 2787df2b-e9d3-440e-bfd0-841a46a9835f
ms.openlocfilehash: 6f1e204c87a6bc940227416696e3cee233271e64
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213869"
---
# <a name="cancellation_token-class"></a>cancellation_token — Klasa

`cancellation_token`Klasa reprezentuje możliwość ustalenia, czy żądanie zostało anulowane przez pewne operacje. Dany token może być skojarzony z `task_group` , `structured_task_group` lub `task` w celu zapewnienia niejawnego anulowania. Może być również sondowany w celu anulowania lub mieć zarejestrowane wywołanie zwrotne dla if i po `cancellation_token_source` anulowaniu skojarzonego elementu.

## <a name="syntax"></a>Składnia

```cpp
class cancellation_token;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[cancellation_token](#ctor)||
|[~ cancellation_token destruktor](#dtor)||

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[deregister_callback](#deregister_callback)|Usuwa wywołanie zwrotne uprzednio zarejestrowane za pomocą `register` metody w oparciu o `cancellation_token_registration` obiekt zwrócony w momencie rejestracji.|
|[is_cancelable](#is_cancelable)|Zwraca wskazanie, czy ten token może być anulowany, czy nie.|
|[is_canceled](#is_canceled)|Zwraca wartość **`true`** , jeśli token został anulowany.|
|[brak](#none)|Zwraca token anulowania, który nigdy nie może podlegać anulowaniu.|
|[register_callback](#register_callback)|Rejestruje funkcję wywołania zwrotnego z tokenem. Jeśli token zostanie anulowany, wywołanie zwrotne zostanie wykonane. Należy pamiętać, że jeśli token jest już anulowany w punkcie, w którym ta metoda jest wywoływana, wywołanie zwrotne zostanie wykonane natychmiast i synchronicznie.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator! =](#operator_neq)||
|[operator =](#operator_eq)||
|[operator = =](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`cancellation_token`

## <a name="requirements"></a>Wymagania

**Nagłówek:** pplcancellation_token. h

**Przestrzeń nazw:** współbieżność

## <a name="cancellation_token"></a><a name="dtor"></a>~ cancellation_token

```cpp
~cancellation_token();
```

## <a name="cancellation_token"></a><a name="ctor"></a>cancellation_token

```cpp
cancellation_token(const cancellation_token& _Src);

cancellation_token(cancellation_token&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Cancellation_token, które mają być kopiowane lub przenoszone.

## <a name="deregister_callback"></a><a name="deregister_callback"></a>deregister_callback

Usuwa wywołanie zwrotne uprzednio zarejestrowane za pomocą `register` metody w oparciu o `cancellation_token_registration` obiekt zwrócony w momencie rejestracji.

```cpp
void deregister_callback(const cancellation_token_registration& _Registration) const;
```

### <a name="parameters"></a>Parametry

*_Registration*<br/>
`cancellation_token_registration`Obiekt odpowiadający wywołaniu zwrotnym do wyrejestrowania. Token ten musiał zostać wcześniej zwrócony z wywołania `register` metody.

## <a name="is_cancelable"></a><a name="is_cancelable"></a>is_cancelable

Zwraca wskazanie, czy ten token może być anulowany, czy nie.

```cpp
bool is_cancelable() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskazanie, czy ten token może być anulowany, czy nie.

## <a name="is_canceled"></a><a name="is_canceled"></a>is_canceled

Zwraca wartość **`true`** , jeśli token został anulowany.

```cpp
bool is_canceled() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość **`true`** , jeśli token został anulowany; w przeciwnym razie wartość **`false`** .

## <a name="none"></a><a name="none"></a>dawaj

Zwraca token anulowania, który nigdy nie może podlegać anulowaniu.

```cpp
static cancellation_token none();
```

### <a name="return-value"></a>Wartość zwracana

Token anulowania, którego nie można anulować.

## <a name="operator"></a><a name="operator_neq"></a>operator! =

```cpp
bool operator!= (const cancellation_token& _Src) const;
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
`cancellation_token`Do porównania.

### <a name="return-value"></a>Wartość zwracana

## <a name="operator"></a><a name="operator_eq"></a>operator =

```cpp
cancellation_token& operator= (const cancellation_token& _Src);

cancellation_token& operator= (cancellation_token&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
`cancellation_token`Do przypisania.

### <a name="return-value"></a>Wartość zwracana

## <a name="operator"></a><a name="operator_eq_eq"></a>operator = =

```cpp
bool operator== (const cancellation_token& _Src) const;
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
`cancellation_token`Do porównania.

### <a name="return-value"></a>Wartość zwracana

## <a name="register_callback"></a><a name="register_callback"></a>register_callback

Rejestruje funkcję wywołania zwrotnego z tokenem. Jeśli token zostanie anulowany, wywołanie zwrotne zostanie wykonane. Należy pamiętać, że jeśli token jest już anulowany w punkcie, w którym ta metoda jest wywoływana, wywołanie zwrotne zostanie wykonane natychmiast i synchronicznie.

```cpp
template<typename _Function>
::Concurrency::cancellation_token_registration register_callback(const _Function& _Func) const;
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ obiektu funkcji, który zostanie wywołany ponownie po `cancellation_token` anulowaniu.

*_Func*<br/>
Obiekt funkcji, który zostanie wywołany ponownie po `cancellation_token` anulowaniu.

### <a name="return-value"></a>Wartość zwracana

`cancellation_token_registration`Obiekt, który można wykorzystać w `deregister` metodzie do wyrejestrowania wcześniej zarejestrowanego wywołania zwrotnego i uniemożliwić jego nabycie. Metoda zgłosi wyjątek [invalid_operation](invalid-operation-class.md) , jeśli jest wywoływana na `cancellation_token` obiekcie, który został utworzony za pomocą metody [cancellation_token:: none](#none) .

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
