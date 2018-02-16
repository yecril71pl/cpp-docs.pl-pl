---
title: Namespace platform::details | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Details
dev_langs:
- C++
helpviewer_keywords:
- Platform::Details Namespace
ms.assetid: e13c1f93-c823-4f0f-a3ee-2429bfd184db
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 41dd178e539da57d0df05440eeb896112d2ce3aa
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="platformdetails-namespace"></a>Namespace platform::details
Ta przestrzeń nazw jest przeznaczony tylko do użytku wewnętrznego i nie mają być używane do tworzenia aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
  
namespace Platform {  
   namespace Details {  
}}  
```  
  
### <a name="members"></a>Elementy członkowskie  
 Mimo że ta przestrzeń nazw jest przeznaczony do użytku wewnętrznego, przeglądarki można wyświetlić następujące elementy członkowskie tej przestrzeni nazw.  
  
|Nazwa|Uwagi|  
|----------|------------|  
|Konsola|Klasa. Wyświetla dane wyjściowe w testach jednostkowych.|  
|_GUID|Struct|  
|Sterty|Class|  
|HeapAllocationTrackingLevel|Wyliczenie|  
|HeapEntryHandler|Delegate|  
|IActivationFactory|Interface|  
|IAgileObject|Interface|  
|IClassFactory|Interface|  
|IEquatable|Interface|  
|IPrintable|Interface|  
|Słabego odwołania|Interface|  
|IWeakReferenceSource|Interface|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Platform`  
  
### <a name="requirements"></a>Wymagania  
 **Metadane:** platform.winmd  
  
 **Namespace:** Platform::Details  
  
## <a name="see-also"></a>Zobacz też  
 [Namespace platformy](platform-namespace-c-cx.md)