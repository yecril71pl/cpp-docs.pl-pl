---
title: Klasa wartości platform::sizet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformSizeT::SizeT constructor
dev_langs:
- C++
helpviewer_keywords:
- Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f60349203ce55a927ffac3d095988e5198bedd87
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601924"
---
# <a name="platformsizet-value-class"></a>Klasa wartości Platform::SizeT
Reprezentuje rozmiar obiektu. SizeT jest typem danych bez znaku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
public ref class SizeT sealed : ValueType  
```  
  
### <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[Konstruktor SizeT::SizeT](#ctor)|Inicjuje nowe wystąpienie klasy z określoną wartością.|  
  
### <a name="requirements"></a>Wymagania  
 **Minimalna obsługiwana klienta:** systemu Windows 8  
  
 **Minimalna obsługiwana serwera:** systemu Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadane:** platform.winmd  

 ## <a name="ctor"></a>  Konstruktor SizeT::SizeT
Inicjuje nowe wystąpienie klasy SizeT z określoną wartością.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
SizeT( uint32 value1 );   SizeT( void* value2 );  
```  
  
### <a name="parameters"></a>Parametry  
 Wartość1  
 Wartość nieoznaczona 32-bitowych.  
  
 Wartość2  
 Wskaźnik na wartość nieoznaczona 32-bitowych.  
  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)