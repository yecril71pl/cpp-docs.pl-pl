---
title: Eksportuj | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.export
dev_langs: C++
helpviewer_keywords: export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7a3229b1cc924c0268bf9a79df53bc18ce2684a1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="export"></a>export
Powoduje, że struktura danych mają być umieszczone w pliku .idl.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
[export]  
  
```  
  
## <a name="remarks"></a>Uwagi  
 **Wyeksportować** atrybutu C++ powoduje, że struktura danych można umieścić w pliku .idl i będzie dostępna w bibliotece typów w formacie zgodnego pliku binarnego, dzięki którym można używać z dowolnego języka.  
  
 Nie można zastosować **wyeksportować** atrybutu do klasy, nawet jeśli klasa zawiera tylko publiczne elementy członkowskie (odpowiednik `struct`).  
  
 Podczas eksportowania nienazwane `enum`s lub `struct`s, zostaną one podanej o nazwach zaczynających **__unnamed***x*, gdzie *x* jest to numer kolejny.  
  
 Definicje typów prawidłowy eksportu są typów podstawowych, struktury, złożenia, wyliczenia lub wpisz identyfikatorów.  Zobacz [typedef](http://msdn.microsoft.com/library/windows/desktop/aa367287) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia **wyeksportować** atrybutu:  
  
```  
// cpp_attr_ref_export.cpp  
// compile with: /LD  
[module(name="MyLibrary")];  
  
[export]  
struct MyStruct {  
   int i;  
};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Unia**, `typedef`, `enum`, `struct`, lub`interface`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty kompilatora](../windows/compiler-attributes.md)   
 [Element TypeDef, Enum, Unii i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
