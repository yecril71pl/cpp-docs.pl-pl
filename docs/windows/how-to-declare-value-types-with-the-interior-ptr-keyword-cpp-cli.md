---
title: "Porady: deklarowanie typów wartości za pomocą słowa kluczowego interior_ptr (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- _ptr keyword
- value types, declaring
ms.assetid: 49eea66e-eeba-49bd-95b0-ba297be436e3
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4b42cbbbc175b3d48baa7b7b2e1c1a5b0e4cbf15
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-declare-value-types-with-the-interiorptr-keyword-ccli"></a>Poradnik: Deklarowanie typów wartości za pomocą słowa kluczowego interior_ptr (C++/CLI)
`interior_ptr` Może być używany z typem wartości.  
  
> [!IMPORTANT]
>  Ta funkcja językowa jest obsługiwana przez **/CLR** — opcja kompilatora, ale nie przez **/ZW** — opcja kompilatora.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Następujące C + +/ CLI pokazano sposób użycia `interior_ptr` z typem wartości.  
  
### <a name="code"></a>Kod  
  
```  
// interior_ptr_value_types.cpp  
// compile with: /clr  
value struct V {  
   V(int i) : data(i){}  
   int data;  
};  
  
int main() {  
   V v(1);  
   System::Console::WriteLine(v.data);  
  
   // pointing to a value type  
   interior_ptr<V> pv = &v;  
   pv->data = 2;  
  
   System::Console::WriteLine(v.data);  
   System::Console::WriteLine(pv->data);  
  
   // pointing into a value type  
   interior_ptr<int> pi = &v.data;  
   *pi = 3;  
   System::Console::WriteLine(*pi);  
   System::Console::WriteLine(v.data);  
   System::Console::WriteLine(pv->data);  
}  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```  
1  
2  
2  
3  
3  
3  
```  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W typie wartości `this` wskaźnika daje w wyniku interior_ptr.  
  
 W treści niestatycznej funkcji członkowskiej typu wartości `V`, `this` jest wyrażeniem typu `interior_ptr<V>` którego wartość jest adresem obiektu, dla której wywołano tę funkcję.  
  
### <a name="code"></a>Kod  
  
```  
// interior_ptr_value_types_this.cpp  
// compile with: /clr /LD  
value struct V {  
   int data;  
   void f() {  
      interior_ptr<V> pv1 = this;  
      // V* pv2 = this;   error  
   }  
};  
```  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład przedstawia sposób użycia operator address-of ze statycznymi elementami członkowskimi.  
  
 Adres statyczny element członkowski typu Visual C++ daje wskaźnik natywny.  Adresu elementu członkowskiego typu wartości statycznej jest wskaźnik zarządzanych, ponieważ element członkowski typu wartość jest przydzielony na stosie środowiska uruchomieniowego i mogą być przenoszone przez moduł garbage collector.  
  
### <a name="code"></a>Kod  
  
```  
// interior_ptr_value_static.cpp  
// compile with: /clr  
using namespace System;  
value struct V { int i; };  
  
ref struct G {  
   static V v = {22};   
   static int i = 23;   
   static String^ pS = "hello";   
};  
  
int main() {  
   interior_ptr<int> p1 = &G::v.i;  
   Console::WriteLine(*p1);  
  
   interior_ptr<int> p2 = &G::i;  
   Console::WriteLine(*p2);  
  
   interior_ptr<String^> p3 = &G::pS;  
   Console::WriteLine(*p3);  
}  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```  
22  
23  
hello  
```  
  
## <a name="see-also"></a>Zobacz też  
 [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)