---
title: "Błąd narzędzi konsolidatora LNK1256 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- xml
- LNK1256
dev_langs:
- C++
helpviewer_keywords:
- LNK1256
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bbbb14e4f4fdef63b58bdef5ecafcfe0b045f412
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1256"></a>Błąd narzędzi konsolidatora LNK1256
Operacja ALINK nie powiodła się: Przyczyna  
  
 Typową przyczyną LNK1256 jest nieprawidłowy numer wersji dla zestawu. Wartość 65535 nie jest dozwolona dla dowolnej części numer wersji zestawu. Prawidłowy zakres dla wersji zestawu to 0 – 65534.  
  
 LNK1256 może również być spowodowany ALINK nie można odnaleźć nazwanego kontener klucza. Usuń kontener kluczy i dodaj go ponownie do silnej nazwy dostawcy usług Kryptograficznych za pomocą [Sn.exe (narzędzie silnej nazwy)](/dotnet/framework/tools/sn-exe-strong-name-tool).  
  
 Inną przyczyną LNK1256 niezgodność wersji między konsolidatora i Alink.dll. Przyczyną może być uszkodzenie instalacji programu Visual Studio. Użyj **programy i funkcje** w Panelu sterowania systemu Windows do naprawy lub ponownej instalacji programu Visual Studio.  
  
 Poniższy przykład generuje LNK1256:  
  
```  
// LNK1256.cpp  
// compile with: /clr /LD  
// LNK1256 expected  
[assembly:System::Reflection::AssemblyVersionAttribute("1.0.65535")];  
public class CMyClass {  
public:  
   int value;  
};  
```