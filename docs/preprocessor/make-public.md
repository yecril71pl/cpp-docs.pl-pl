---
title: make_public | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.make_public
- make_public_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, make_public
- make_public pragma
ms.assetid: c3665f4d-268a-4932-9661-c37c8ae6a341
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27db5ac934973178e2485327090ed70f994becec
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="makepublic"></a>make_public
Informuje, że typ macierzysty powinien publicznego zestawu dostępności.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma make_public(type)  
```  
  
### <a name="parameters"></a>Parametry  
 `type` jest nazwa typu mają publicznego zestawu dostępności.  
  
## <a name="remarks"></a>Uwagi  
`make_public` jest przydatne w przypadku gdy jest typem natywnym, który chcesz odwołać z pliku .h, którego nie można zmienić. Jeśli chcesz użyć typu macierzystego w sygnaturze funkcji publicznych w typie z widocznością publicznego zestawu, typu macierzystego musi mieć również dostępność publicznego zestawu lub kompilator zgłosi ostrzeżenie.  
  
`make_public` musi być określony w zakresie globalnym i działa tylko w od punktu, w którym jest zadeklarowany za pomocą na końcu pliku kodu źródłowego.  
  
Typ macierzysty może być jawnie lub niejawnie prywatne; zobacz [widoczność typów](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
Poniższy przykład jest zawartość pliku .h, który zawiera definicje dla dwóch struktury macierzystego.  
  
```cpp  
// make_public_pragma.h  
struct Native_Struct_1 { int i; };  
struct Native_Struct_2 { int i; };  
```  
  
## <a name="example"></a>Przykład  
Poniższy przykład kodu wykorzystuje plik nagłówka i wskazuje, że chyba że jawnie oznaczone natywnego struktury jako public, przy użyciu `make_public`, kompilator wygeneruje ostrzeżenie podczas próby użycia natywnego struktury w sygnaturze funkcji publicznej w publiczny typ zarządzany.  
  
```cpp  
// make_public_pragma.cpp  
// compile with: /c /clr /W1  
#pragma warning (default : 4692)  
#include "make_public_pragma.h"  
#pragma make_public(Native_Struct_1)  
  
public ref struct A {  
   void Test(Native_Struct_1 u) {u.i = 0;}   // OK  
   void Test(Native_Struct_2 u) {u.i = 0;}   // C4692  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)