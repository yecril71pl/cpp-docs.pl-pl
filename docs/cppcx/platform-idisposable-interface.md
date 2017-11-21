---
title: Interfejs platform::IDisposable | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VCCORLIB/Platform::IDisposable
dev_langs: C++
helpviewer_keywords: Platform::IDisposable Interface
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 0bc36087532bbac86b5891408fc3e4bea30c0256
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="platformidisposable-interface"></a>Interfejs platform::IDisposable
Należy użyć, aby zwolnić zasoby niezarządzane.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
public interface class IDisposable  
```  
  
## <a name="attributes"></a>Atrybuty  
 **GuidAttribute**("de0cbaea-8065-4a45-b196-c9d443f9bab3")  
  
 **VersionAttribute**(NTDDI_WIN8)  
  
### <a name="members"></a>Elementy członkowskie  
 Interfejs IDisposable dziedziczy po interfejsie IUnknown. Interfejs IDisposable ma również następujące typy elementów członkowskich:  
  
 **Metody**  
  
 Interfejs IDisposable, ma następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|Metoda Dispose|Należy użyć, aby zwolnić zasoby niezarządzane.|  
  
### <a name="requirements"></a>Wymagania  
 **Minimalna obsługiwana klienta:** systemu Windows 8  
  
 **Minimalna obsługiwana serwera:** systemu Windows Server 2012  
  
 **Namespace:** platformy