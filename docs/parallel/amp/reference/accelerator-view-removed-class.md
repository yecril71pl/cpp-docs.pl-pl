---
title: accelerator_view_removed — klasa
ms.date: 03/27/2019
f1_keywords:
- accelerator_view_removed
- AMPRT/accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed::accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed::get_view_removed_reason
helpviewer_keywords:
- AMPRT/Concurrency::accelerator_view_removed::accelerator_view_removed Class
ms.assetid: 262446de-311c-454e-a5ed-e2aaced0d88a
ms.openlocfilehash: 09f534a90f3191025c3ce99d07a462908387c676
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58564954"
---
# <a name="acceleratorviewremoved-class"></a>accelerator_view_removed — klasa

Wyjątek, który jest generowany, kiedy wywołanie DirectX nie powiedzie się z powodu przekroczenia limitu czasu Windows mechanizm wykrywania i odzyskiwania.

## <a name="syntax"></a>Składnia

```
class accelerator_view_removed : public runtime_exception;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[accelerator_view_removed Constructor](#ctor)|Inicjuje nowe wystąpienie klasy `accelerator_view_removed` klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get_view_removed_reason](#get_view_removed_reason)|Zwraca kod błędu HRESULT wskazujący przyczynę `accelerator_view` usunięcie obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt.h

**Namespace:** Współbieżność

## <a name="ctor"></a> accelerator_view_removed

Inicjuje nowe wystąpienie klasy [accelerator_view_removed](accelerator-view-removed-class.md) klasy.

### <a name="syntax"></a>Składnia

```
explicit accelerator_view_removed(
    const char * message,
    HRESULT view_removed_reason ) throw();

explicit accelerator_view_removed(
    HRESULT view_removed_reason ) throw();
```

### <a name="parameters"></a>Parametry

*komunikat*<br/>
Opis błędu.

*view_removed_reason*<br/>
Kod błędu HRESULT wskazujący przyczynę usunięcia `accelerator_view` obiektu.

### <a name="return-value"></a>Wartość zwracana

Nowe wystąpienie klasy `accelerator_view_removed` klasy.

## <a name="getviewremovedreason"></a>get_view_removed_reason

Zwraca kod błędu HRESULT wskazujący przyczynę `accelerator_view` usunięcie obiektu.

### <a name="syntax"></a>Składnia

```
HRESULT get_view_removed_reason() const throw();
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
