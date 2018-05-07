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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8c69bf34a7965c098f6a656907071e0899b785b4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="platformsizet-value-class"></a>Klasa wartości Platform::SizeT
Reprezentuje rozmiar obiektu. SizeT ma typ danych bez znaku.  
  
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
Inicjuje nowe wystąpienie klasy SizeT o określonej wartości.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
SizeT( uint32 value1 );   SizeT( void* value2 );  
```  
  
### <a name="parameters"></a>Parametry  
 Wartość1  
 Wartość 32-bitowe bez znaku.  
  
 Wartość2  
 Wskaźnik do niepodpisanego 32-bitową wartość.  
  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)