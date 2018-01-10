---
title: _SCL_SECURE_NO_WARNINGS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
dev_langs: C++
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 288af808dfa714c10eeba1f11738cf9db31d70d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS
Wywoływanie jednej z metod potencjalnie niebezpiecznych w standardowej bibliotece C++ spowoduje [C4996 ostrzeżenie kompilatora (poziom 3)](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Aby wyłączyć to ostrzeżenie, zdefiniuj makra **_SCL_SECURE_NO_WARNINGS** w kodzie:  
  
```  
#define _SCL_SECURE_NO_WARNINGS  
```  
  
## <a name="remarks"></a>Uwagi  
 Inne sposoby wyłączenia ostrzeżenie C4996 obejmują:  
  
-   Przy użyciu [/D (definicje preprocesora)](../build/reference/d-preprocessor-definitions.md) — opcja kompilatora:  
  
 ```  
    cl /D_SCL_SECURE_NO_WARNINGS [other compiler options] myfile.cpp  
```  
  
-   Przy użyciu [/w](../build/reference/compiler-option-warning-level.md) — opcja kompilatora:  
  
 ```  
    cl /wd4996 [other compiler options] myfile.cpp  
```  
  
-   Przy użyciu [ostrzeżenie #pragma](../preprocessor/warning.md) dyrektywy:  
  
 ```  
 #pragma warning(disable:4996)  
```  
  
 Ponadto możesz ręcznie zmienić poziom ostrzeżenia C4996 z **/w\<l >\< n>**  — opcja kompilatora. Na przykład, aby ustawić ostrzeżenie C4996 poziom 4:  
  
```  
cl /w44996 [other compiler options] myfile.cpp  
```  
  
 Aby uzyskać więcej informacji, zobacz [/w, /W0, /W1, /W2, /W3, / W4, /w1, /w2, /w3, / W4, / Wall, /wd, / możemy /wo, /Wv, wx (poziom ostrzegawczy)](../build/reference/compiler-option-warning-level.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczne biblioteki: Standardowa biblioteka C++](../standard-library/safe-libraries-cpp-standard-library.md)

