---
title: progress_reporter — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- progress_reporter
- PPLTASKS/concurrency::progress_reporter
- PPLTASKS/concurrency::progress_reporter::progress_reporter
- PPLTASKS/concurrency::progress_reporter::report
dev_langs:
- C++
helpviewer_keywords:
- progress_reporter class
ms.assetid: b836efab-2d05-4649-b6fa-d15236f1f813
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d4a1b76966216a6dc7b2e7249bddb1ac629376f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016770"
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
|[Raport](#report)|Wysyła raport o postępie do akcji lub operacji asynchronicznej z którym powiązany jest ten program raportujący postęp.|  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
