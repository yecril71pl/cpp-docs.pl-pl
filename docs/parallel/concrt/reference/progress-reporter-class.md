---
title: "progress_reporter — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aaac198ab17c33330cbc63d951bfbee97c1d4e94
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="progressreporter-class"></a>progress_reporter — Klasa
Klasa osoby zgłaszającej postępu umożliwia raportowanie postępu powiadomienia określonego typu. Każdy obiekt progress_reporter — jest powiązany z określonej akcji asynchronicznej lub operacji.  
  
## <a name="syntax"></a>Składnia  
  
```
template<typename _ProgressType>
class progress_reporter;
```  
  
#### <a name="parameters"></a>Parametry  
 `_ProgressType`  
 Typ ładunku każdego powiadomienie o postępie zgłoszone za pośrednictwem osoby zgłaszającej postępu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[progress_reporter](#ctor)||  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Raport](#report)|Wysyła raport postępu akcji asynchronicznej lub powiązane tej osoby zgłaszającej postęp operacji.|  
  
## <a name="remarks"></a>Uwagi  
 Ten typ jest dostępna tylko do aplikacji środowiska wykonawczego systemu Windows.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `progress_reporter`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ppltasks.h  
  
 **Namespace:** współbieżności  
  
##  <a name="ctor"></a> progress_reporter — 

```
progress_reporter();
```  
  
##  <a name="report">Raport</a> 

 Wysyła raport postępu akcji asynchronicznej lub powiązane tej osoby zgłaszającej postęp operacji.  
  
```
void report(const _ProgressType& val) const;
```  
  
### <a name="parameters"></a>Parametry  
 `val`  
 Ładunek do raportów za pośrednictwem powiadomienie o postępie.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
