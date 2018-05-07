---
title: Ostrzeżenie LNK4247 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4247
dev_langs:
- C++
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6096bbfba9c60d8ed28aa660d078cd155f0316a3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4247"></a>Ostrzeżenie LNK4247 narzędzi konsolidatora
punkt wejścia "decorated_function_name" ma już atrybut wątku; Zignorowano 'atrybut'  
  
 Punkt wejścia określony za pomocą [/Entry (Symbol punktu wejścia)](../../build/reference/entry-entry-point-symbol.md), ma atrybut wątkowości, ale [/CLRTHREADATTRIBUTE (Ustaw CLR wątku atrybut)](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md) również została określona z innego modelu wątkowości.  
  
 Konsolidator ignorowany podana wartość z /CLRTHREADATTRIBUTE.  
  
 Aby usunąć to ostrzeżenie:  
  
-   Usuń /CLRTHREADATTRIBUTE z kompilacji.  
  
-   Usuń atrybut z pliku kodu źródłowego.  
  
-   Usunąć zarówno atrybut źródłowy i /CLRTHREADATTRIBUTE z kompilacji, a następnie zaakceptuj domyślny model wątkowości CLR.  
  
-   Wartość przekazana do /CLRTHREADATTRIBUTE, należy zmienić tak, aby go zgadza się z atrybutem w źródle.  
  
-   Zmienić atrybutu w źródle, w taki sposób, że akceptuje wartości przekazanych do /CLRTHREADATTRIBUTE.  
  
 Poniższy przykład generuje LNK4247  
  
```  
// LNK4247.cpp  
// compile with: /clr /c  
// post-build command: link /CLRTHREADATTRIBUTE:STA LNK4247.obj /entry:functionTitle /SUBSYSTEM:Console  
 [System::MTAThreadAttribute]  
void functionTitle (){}  
```