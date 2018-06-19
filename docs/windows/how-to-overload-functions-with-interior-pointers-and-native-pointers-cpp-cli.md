---
title: 'Porady: funkcje przeładowania z wewnętrznymi i Natywnymi wskaźnikami (C + +/ CLI) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Functions with interior and native pointers, overloading
ms.assetid: d70df625-4aad-457c-84f5-70a0a290cc1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7e3bc7e5fca6a34f9847c913e92e523b2898068f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874866"
---
# <a name="how-to-overload-functions-with-interior-pointers-and-native-pointers-ccli"></a>Poradnik: Funkcje przeładowania z wewnętrznymi i natywnymi wskaźnikami (C++/CLI)
W zależności od tego, czy typ parametru jest wskaźnik wewnętrzny lub wskaźnik natywny można przeciążać funkcji.  
  
> [!IMPORTANT]
>  Ta funkcja językowa jest obsługiwana przez **/CLR** — opcja kompilatora, ale nie przez **/ZW** — opcja kompilatora.  
  
## <a name="example"></a>Przykład  
  
### <a name="code"></a>Kod  
  
```  
// interior_ptr_overload.cpp  
// compile with: /clr  
using namespace System;  
  
// C++ class  
struct S {  
   int i;  
};  
  
// managed class  
ref struct G {  
   int i;  
};  
  
// can update unmanaged storage  
void f( int* pi ) {  
   *pi = 10;  
   Console::WriteLine("in f( int* pi )");  
}  
  
// can update managed storage  
void f( interior_ptr<int> pi ) {  
   *pi = 10;   
   Console::WriteLine("in f( interior_ptr<int> pi )");  
}  
  
int main() {  
   S *pS = new S;   // C++ heap  
   G ^pG = gcnew G;   // common language runtime heap  
   f( &pS->i );  
   f( &pG->i );  
};  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```  
in f( int* pi )  
in f( interior_ptr<int> pi )  
```  
  
## <a name="see-also"></a>Zobacz też  
 [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)