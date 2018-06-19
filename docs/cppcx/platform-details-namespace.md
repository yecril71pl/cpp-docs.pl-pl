---
title: Namespace platform::details | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Details
dev_langs:
- C++
helpviewer_keywords:
- Platform::Details Namespace
ms.assetid: e13c1f93-c823-4f0f-a3ee-2429bfd184db
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aa3de0d0f21c1155e550528287c03ae707f44ea2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33087654"
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
|Interfejsu IEquatable|Interface|  
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