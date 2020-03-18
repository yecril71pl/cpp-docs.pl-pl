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
ms.openlocfilehash: 34743ce48510eec9d8f7862e5ed951a722932962
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422242"
---
# <a name="cancellation_token-class"></a>cancellation_token — Klasa

Klasa `cancellation_token` reprezentuje możliwość ustalenia, czy żądana operacja została anulowana. Dany token może być skojarzony z `task_group`, `structured_task_group`lub `task` w celu zapewnienia niejawnego anulowania. Może być również sondowany w celu anulowania lub mieć zarejestrowane wywołanie zwrotne dla if i po anulowaniu skojarzonego `cancellation_token_source`.

## <a name="syntax"></a>Składnia

```cpp
class cancellation_token;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[cancellation_token](#ctor)||
|[~ cancellation_token destruktor](#dtor)||

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[deregister_callback](#deregister_callback)|Usuwa wywołanie zwrotne uprzednio zarejestrowane za pomocą metody `register` w oparciu o obiekt `cancellation_token_registration` zwrócony w momencie rejestracji.|
|[is_cancelable](#is_cancelable)|Zwraca wskazanie, czy ten token może być anulowany, czy nie.|
|[is_canceled](#is_canceled)|Zwraca **wartość PRAWDA** , jeśli token został anulowany.|
|[dawaj](#none)|Zwraca token anulowania, który nigdy nie może podlegać anulowaniu.|
|[register_callback](#register_callback)|Rejestruje funkcję wywołania zwrotnego z tokenem. Jeśli token zostanie anulowany, wywołanie zwrotne zostanie wykonane. Należy pamiętać, że jeśli token jest już anulowany w punkcie, w którym ta metoda jest wywoływana, wywołanie zwrotne zostanie wykonane natychmiast i synchronicznie.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operator =](#operator_eq)||
|[operator = =](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`cancellation_token`

## <a name="requirements"></a>Wymagania

**Nagłówek:** pplcancellation_token. h

**Przestrzeń nazw:** współbieżność

## <a name="dtor"></a>~ cancellation_token

```cpp
~cancellation_token();
```

## <a name="ctor"></a>cancellation_token

```cpp
cancellation_token(const cancellation_token& _Src);

cancellation_token(cancellation_token&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Cancellation_token, które mają być kopiowane lub przenoszone.

## <a name="deregister_callback"></a>deregister_callback

Usuwa wywołanie zwrotne uprzednio zarejestrowane za pomocą metody `register` w oparciu o obiekt `cancellation_token_registration` zwrócony w momencie rejestracji.

```cpp
void deregister_callback(const cancellation_token_registration& _Registration) const;
```

### <a name="parameters"></a>Parametry

*_Registration*<br/>
Obiekt `cancellation_token_registration` odpowiadający wywołaniu zwrotnym do wyrejestrowania. Token ten musiał zostać wcześniej zwrócony z wywołania metody `register`.

## <a name="is_cancelable"></a>is_cancelable

Zwraca wskazanie, czy ten token może być anulowany, czy nie.

```cpp
bool is_cancelable() const;
```

### <a name="return-value"></a>Wartość zwrócona

Wskazanie, czy ten token może być anulowany, czy nie.

## <a name="is_canceled"></a>is_canceled

Zwraca **wartość PRAWDA** , jeśli token został anulowany.

```cpp
bool is_canceled() const;
```

### <a name="return-value"></a>Wartość zwrócona

Wartość **true** , jeśli token został anulowany; w przeciwnym razie wartość **false**.

## <a name="none"></a>dawaj

Zwraca token anulowania, który nigdy nie może podlegać anulowaniu.

```cpp
static cancellation_token none();
```

### <a name="return-value"></a>Wartość zwrócona

Token anulowania, którego nie można anulować.

## <a name="operator_neq"></a>operator! =

```cpp
bool operator!= (const cancellation_token& _Src) const;
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
`cancellation_token` do porównania.

### <a name="return-value"></a>Wartość zwrócona

## <a name="operator_eq"></a>operator =

```cpp
cancellation_token& operator= (const cancellation_token& _Src);

cancellation_token& operator= (cancellation_token&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
`cancellation_token` do przypisania.

### <a name="return-value"></a>Wartość zwrócona

## <a name="operator_eq_eq"></a>operator = =

```cpp
bool operator== (const cancellation_token& _Src) const;
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
`cancellation_token` do porównania.

### <a name="return-value"></a>Wartość zwrócona

## <a name="register_callback"></a>register_callback

Rejestruje funkcję wywołania zwrotnego z tokenem. Jeśli token zostanie anulowany, wywołanie zwrotne zostanie wykonane. Należy pamiętać, że jeśli token jest już anulowany w punkcie, w którym ta metoda jest wywoływana, wywołanie zwrotne zostanie wykonane natychmiast i synchronicznie.

```cpp
template<typename _Function>
::Concurrency::cancellation_token_registration register_callback(const _Function& _Func) const;
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ obiektu funkcji, który zostanie wywołany ponownie po anulowaniu tego `cancellation_token`.

*_Func*<br/>
Obiekt funkcji, który zostanie wywołany ponownie po anulowaniu tego `cancellation_token`.

### <a name="return-value"></a>Wartość zwrócona

Obiekt `cancellation_token_registration`, którego można użyć w metodzie `deregister` do wyrejestrowania wcześniej zarejestrowanego wywołania zwrotnego i uniemożliwić jego napisanie. Metoda zgłosi wyjątek [invalid_operation](invalid-operation-class.md) , jeśli jest wywoływana na obiekcie `cancellation_token`, który został utworzony za pomocą metody [cancellation_token:: none](#none) .

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
