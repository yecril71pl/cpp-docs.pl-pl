---
title: "progress_reporter — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- progress_reporter
- PPLTASKS/concurrency::progress_reporter
- PPLTASKS/concurrency::progress_reporter::progress_reporter
- PPLTASKS/concurrency::progress_reporter::report
dev_langs: C++
helpviewer_keywords: progress_reporter class
ms.assetid: b836efab-2d05-4649-b6fa-d15236f1f813
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1dcdba2e5242dcd750eea42b61575ebea921d7b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
|[progress_reporter —](#ctor)||  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Raport](#report)|Wysyła raport postępu akcji asynchronicznej lub powiązane tej osoby zgłaszającej postęp operacji.|  
  
## <a name="remarks"></a>Uwagi  
 Ten typ jest dostępna tylko do aplikacji ze Sklepu Windows.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `progress_reporter`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ppltasks.h  
  
 **Namespace:** współbieżności  
  
##  <a name="ctor"></a>progress_reporter — 

```
progress_reporter();
```  
  
##  <a name="report"></a>Raport 

 Wysyła raport postępu akcji asynchronicznej lub powiązane tej osoby zgłaszającej postęp operacji.  
  
```
void report(const _ProgressType& val) const;
```  
  
### <a name="parameters"></a>Parametry  
 `val`  
 Ładunek do raportów za pośrednictwem powiadomienie o postępie.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
