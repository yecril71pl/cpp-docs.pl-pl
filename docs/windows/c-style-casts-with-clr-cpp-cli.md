---
title: "Z - clr Rzutowań w stylu języka C (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: C-style casts and /clr
ms.assetid: d2a4401a-156a-4da9-8d12-923743e26913
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e529a40f8eb876791f49559d3970696fdece489d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c-style-casts-with-clr-ccli"></a>Rzutowania w stylu C i kompilator /clr (C++/CLI)
Poniższy temat dotyczy tylko środowiska CLR.  
  
 W przypadku użycia z typów CLR, kompilator próbuje zamapować stylu języka C rzutować rzutowania wymienione poniżej, w następującej kolejności:  
  
1.  Operator const_cast  
  
2.  safe_cast  
  
3.  safe_cast plus operator const_cast  
  
4.  static_cast  
  
5.  static_cast plus operator const_cast  
  
 Jeśli żaden z powyższych rzutowania nie jest prawidłowy, a typ wyrażenia i typ docelowy są typy referencyjne CLR, rzutowania w stylu C mapuje Sprawdzanie czasu wykonywania (instrukcja MSIL castclass). W przeciwnym razie jest nieprawidłowe rzutowanie w stylu języka C i kompilator generuje błąd.  
  
## <a name="remarks"></a>Uwagi  
 Rzutowania w stylu języka C nie jest zalecane. Podczas kompilowania za pomocą [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md), użyj [safe_cast](../windows/safe-cast-cpp-component-extensions.md).  
  
 Poniższy przykład przedstawia C rzutowanie w stylu mapowanego `const_cast`.  
  
```  
// cstyle_casts_1.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct R {};  
int main() {  
   const R^ constrefR = gcnew R();  
   R^ nonconstR = (R^)(constrefR);   
}  
```  
  
 Poniższy przykład przedstawia C rzutowanie w stylu mapowanego `safe_cast`.  
  
```  
// cstyle_casts_2.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   Object ^ o = "hello";  
   String ^ s = (String^)o;  
}  
```  
  
 Poniższy przykład przedstawia C rzutowanie w stylu mapowanego `safe_cast` plus `const_cast`.  
  
```  
// cstyle_casts_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct R {};  
ref struct R2 : public R {};  
  
int main() {  
   const R^ constR2 = gcnew R2();  
   try {  
   R2^ b2DR = (R2^)(constR2);  
   }  
   catch(InvalidCastException^ e) {  
      System::Console::WriteLine("Invalid Exception");  
   }  
}  
```  
  
 Poniższy przykład przedstawia C rzutowanie w stylu mapowanego `static_cast`.  
  
```  
// cstyle_casts_4.cpp  
// compile with: /clr  
using namespace System;  
  
struct N1 {};  
struct N2 {  
   operator N1() {  
      return N1();  
   }  
};  
  
int main() {  
   N2 n2;  
   N1 n1 ;  
   n1 = (N1)n2;  
}  
```  
  
 Poniższy przykład przedstawia C rzutowanie w stylu mapowanego `static_cast` plus `const_cast`.  
  
```  
// cstyle_casts_5.cpp  
// compile with: /clr  
using namespace System;  
struct N1 {};  
  
struct N2 {  
   operator const N1*() {  
      static const N1 n1;  
      return &n1;  
   }  
};  
  
int main() {  
   N2 n2;  
   N1* n1 = (N1*)(const N1*)n2;   // const_cast + static_cast  
}  
```  
  
 Poniższy przykład przedstawia C rzutowanie w stylu mapujący do wyboru czasu wykonywania.  
  
```  
// cstyle_casts_6.cpp  
// compile with: /clr  
using namespace System;  
  
ref class R1 {};  
ref class R2 {};  
  
int main() {  
   R1^ r  = gcnew R1();  
   try {  
      R2^ rr = ( R2^)(r);  
   }  
   catch(System::InvalidCastException^ e) {  
      Console::WriteLine("Caught expected exception");  
   }  
}  
```  
  
 Poniższy przykład zawiera nieprawidłowy C rzutowanie w stylu, co powoduje, że kompilator wydania wystąpił błąd.  
  
```  
// cstyle_casts_7.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   String^s = S"hello";  
   int i = (int)s;   // C2440  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)