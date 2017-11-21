---
title: Namespace platform::METADATA | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VCCORLIB/Platform::Metadata
dev_langs: C++
helpviewer_keywords: Platform::Metadata Namespace
ms.assetid: e3e114d8-a4b0-47f0-865a-9ce9d7212e86
caps.latest.revision: "6"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 7c108dd9435d433076ea2f2c9b573f2ebf3685e3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="platformmetadata-namespace"></a>Namespace platform::METADATA
Ta przestrzeń nazw zawiera atrybuty, które modyfikują deklaracje typów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
  
namespace Platform {  
   namespace Metadata {  
}}  
```  
  
### <a name="members"></a>Elementy członkowskie  
 Mimo że ta przestrzeń nazw jest przeznaczony do użytku wewnętrznego, przeglądarki można wyświetlić następujące elementy członkowskie tej przestrzeni nazw.  
  
|Nazwa|Uwagi|  
|----------|------------|  
|Atrybut|Klasa podstawowa dla atrybutów.|  
|[Atrybut platform::METADATA::DefaultMemberAttribute](../cppcx/platform-metadata-defaultmemberattribute-attribute.md)|Wskazuje preferowaną funkcji do wywołania między kilka możliwych przeciążonej funkcji.|  
|[Atrybut platform::METADATA::FlagsAttribute](../cppcx/platform-metadata-flagsattribute-attribute.md)flagi|Deklaruje wyliczenie jako wyliczenie pól bitowych.<br /><br /> Poniższy przykład przedstawia sposób zastosowania `Flags` atrybutu wyliczenia.<br /><br /> `[Flags] enum class MyEnumeration { enumA = 1, enumB = 2, enumC = 3}`|  
|[Platform::METADATA::RuntimeClassNameAttribute](../cppcx/platform-metadata-runtimeclassname.md)|Zapewnia, że prywatnej klasy ref ma prawidłowe środowisko uruchomieniowe nazwę klasy.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Platform`  
  
### <a name="requirements"></a>Wymagania  
 **Metadane:** platform.winmd  
  
 **Namespace:** Platform::Metadata  
  
## <a name="see-also"></a>Zobacz też  
 [Namespace platformy](platform-namespace-c-cx.md)