---
title: Błąd narzędzi konsolidatora LNK1256 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- xml
- LNK1256
dev_langs:
- C++
helpviewer_keywords:
- LNK1256
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e4039dccb4dc8abd421b4622bbe928931f7f396
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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