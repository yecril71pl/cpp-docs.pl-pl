---
title: progress_reporter — Klasa
ms.date: 11/04/2016
f1_keywords:
- progress_reporter
- PPLTASKS/concurrency::progress_reporter
- PPLTASKS/concurrency::progress_reporter::progress_reporter
- PPLTASKS/concurrency::progress_reporter::report
helpviewer_keywords:
- progress_reporter class
ms.assetid: b836efab-2d05-4649-b6fa-d15236f1f813
ms.openlocfilehash: dac74085278418153ddec502f6257ce13885704d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282542"
---
# <a name="progressreporter-class"></a>progress_reporter — Klasa

Klasa reportera postępu pozwala raportowania powiadomienia o postępie określonego typu. Każdy obiekt progress_reporter jest powiązany z określoną akcją lub operacją asynchroniczną.

## <a name="syntax"></a>Składnia

```
template<typename _ProgressType>
class progress_reporter;
```

#### <a name="parameters"></a>Parametry

*_ProgressType*<br/>
Typ ładunku każdego powiadomienia o postępie zgłoszonego za pomocą reportera postępu.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[progress_reporter](#ctor)||

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[report](#report)|Wysyła raport o postępie do akcji lub operacji asynchronicznej z którym powiązany jest ten program raportujący postęp.|

## <a name="remarks"></a>Uwagi

Ten typ jest dostępny tylko dla aplikacji środowiska wykonawczego Windows.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`progress_reporter`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ppltasks.h

**Namespace:** współbieżności

##  <a name="ctor"></a> progress_reporter —

```
progress_reporter();
```

##  <a name="report"></a> Raport

Wysyła raport o postępie do akcji lub operacji asynchronicznej z którym powiązany jest ten program raportujący postęp.

```
void report(const _ProgressType& val) const;
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Ładunek do zgłoszenia poprzez powiadomienie o postępie.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
