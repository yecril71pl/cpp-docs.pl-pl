---
title: accelerator_view_removed, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- accelerator_view_removed
- AMPRT/accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed:accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed:get_view_removed_reason
dev_langs:
- C++
helpviewer_keywords:
- AMPRT/Concurrency::accelerator_view_removed:accelerator_view_removed Class
ms.assetid: 262446de-311c-454e-a5ed-e2aaced0d88a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e937c2f5afedf1c78a46e864ea0b081ddf18e99d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373304"
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
|[accelerator_view_removed — Konstruktor](#ctor)|Inicjuje nowe wystąpienie klasy `accelerator_view_removed` klasy.|

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

**Namespace:** współbieżności

## <a name="ctor"></a> accelerator_view_removed

Inicjuje nowe wystąpienie klasy [accelerator_view_removed](accelerator-view-removed-class.md) klasy.

### <a name="syntax"></a>Składnia

```
explicit accelerator_view_removed(
    const char * _Message,
    HRESULT _View_removed_reason ) throw();

explicit accelerator_view_removed(
    HRESULT _View_removed_reason ) throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Opis błędu.

*_View_removed_reason*<br/>
Kod błędu HRESULT wskazujący przyczynę usunięcia `accelerator_view` obiektu.

### <a name="return-value"></a>Wartość zwracana

Nowe wystąpienie klasy accelerator_view_removed.

## <a name="get_view_removed_reason_method"></a> get_view_removed_reason

Zwraca kod błędu HRESULT wskazujący przyczynę `accelerator_view` usunięcie obiektu.

### <a name="syntax"></a>Składnia

```
HRESULT get_view_removed_reason() const throw();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
