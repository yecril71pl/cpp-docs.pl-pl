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
ms.openlocfilehash: 23821c91cd4158f6ec3989cdf537a5d8067e8225
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62337521"
---
# <a name="cancellationtoken-class"></a>cancellation_token — Klasa

`cancellation_token` Klasa reprezentuje zdolność do określenia, czy zażądano operacji anulowania. Dany token może być skojarzony z `task_group`, `structured_task_group`, lub `task` aby zapewnić anulowanie niejawne. Również może być sondowany o wykreślenie lub wywołanie zwrotne zarejestrowane dla przypadku, gdy skojarzony `cancellation_token_source` zostało anulowane.

## <a name="syntax"></a>Składnia

```
class cancellation_token;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[cancellation_token](#ctor)||
|[~cancellation_token Destructor](#dtor)||

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[deregister_callback](#deregister_callback)|Usuwa wywołanie zwrotne wcześniej zarejestrowane przez `register` metoda oparta na `cancellation_token_registration` obiecie zwróconym w momencie rejestracji.|
|[is_cancelable](#is_cancelable)|Zwraca wskazanie, czy ten token może być anulowany, czy nie.|
|[is_canceled](#is_canceled)|Zwraca **true** Jeśli token został anulowany.|
|[Brak](#none)|Zwraca token anulowania, który nigdy nie może być przedmiotem anulowania.|
|[register_callback](#register_callback)|Rejestruje funkcję wywołania zwrotnego z tokenem. Jeśli token zostanie anulowany, nastąpi wywołanie zwrotne. Należy pamiętać, że jeśli token jest już anulowany w momencie, gdy ta metoda jest wywoływana, wywołanie zwrotne zostanie wprowadzone natychmiast synchronicznie.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operator=](#operator_eq)||
|[operator==](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`cancellation_token`

## <a name="requirements"></a>Wymagania

**Nagłówek:** pplcancellation_token.h

**Namespace:** współbieżności

##  <a name="dtor"></a> ~ cancellation_token —

```
~cancellation_token();
```

##  <a name="ctor"></a> cancellation_token —

```
cancellation_token(const cancellation_token& _Src);

cancellation_token(cancellation_token&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Cancellation_token, które mają być kopiowane lub przeniesiony.

##  <a name="deregister_callback"></a> deregister_callback

Usuwa wywołanie zwrotne wcześniej zarejestrowane przez `register` metoda oparta na `cancellation_token_registration` obiecie zwróconym w momencie rejestracji.

```
void deregister_callback(const cancellation_token_registration& _Registration) const;
```

### <a name="parameters"></a>Parametry

*_Registration*<br/>
`cancellation_token_registration` Obiekt odpowiadający wywołaniu zwrotnemu zostać wyrejestrowany. Ten token musi być wcześniej zwrócony z wywołania do `register` metody.

##  <a name="is_cancelable"></a> is_cancelable —

Zwraca wskazanie, czy ten token może być anulowany, czy nie.

```
bool is_cancelable() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskazanie, czy ten token może być anulowany, czy nie.

##  <a name="is_canceled"></a> is_canceled —

Zwraca **true** Jeśli token został anulowany.

```
bool is_canceled() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość **true** , jeśli token został anulowany; w przeciwnym razie wartość **false**.

##  <a name="none"></a> Brak

Zwraca token anulowania, który nigdy nie może być przedmiotem anulowania.

```
static cancellation_token none();
```

### <a name="return-value"></a>Wartość zwracana

Token anulowania, który nie może zostać anulowana.

##  <a name="operator_neq"></a> operator! =

```
bool operator!= (const cancellation_token& _Src) const;
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
`cancellation_token` Do porównania.

### <a name="return-value"></a>Wartość zwracana

##  <a name="operator_eq"></a> operator =

```
cancellation_token& operator= (const cancellation_token& _Src);

cancellation_token& operator= (cancellation_token&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
`cancellation_token` Do przypisania.

### <a name="return-value"></a>Wartość zwracana

##  <a name="operator_eq_eq"></a> operator ==

```
bool operator== (const cancellation_token& _Src) const;
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
`cancellation_token` Do porównania.

### <a name="return-value"></a>Wartość zwracana

##  <a name="register_callback"></a> register_callback —

Rejestruje funkcję wywołania zwrotnego z tokenem. Jeśli token zostanie anulowany, nastąpi wywołanie zwrotne. Należy pamiętać, że jeśli token jest już anulowany w momencie, gdy ta metoda jest wywoływana, wywołanie zwrotne zostanie wprowadzone natychmiast synchronicznie.

```
template<typename _Function>
::Concurrency::cancellation_token_registration register_callback(const _Function& _Func) const;
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ obiektu funkcji, który zostanie wywołany ponownie po tym `cancellation_token` zostało anulowane.

*_Func*<br/>
Obiekt funkcji, który zostanie wywołany ponownie po tym `cancellation_token` zostało anulowane.

### <a name="return-value"></a>Wartość zwracana

A `cancellation_token_registration` obiektu, który może być wykorzystywany w `deregister` metodę, aby wyrejestrować wcześniej zarejestrowanego wywołania zwrotnego oraz zapobiegania jego wykonywane. Metoda zgłosi [invalid_operation](invalid-operation-class.md) wyjątek, jeśli jest to `cancellation_token` obiekt, który został utworzony przy użyciu [cancellation_token::none —](#none) metody.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
