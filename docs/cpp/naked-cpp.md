---
title: naked (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- naked_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], naked
- naked __declspec keyword
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1057754b5c98086de42daedd5e7aab70656eba69
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947768"
---
# <a name="naked-c"></a>naked (C++)
**Microsoft Specific**  
  
 Aby funkcje zadeklarowane za pomocą **"naked"** atrybutu, kompilator generuje kod bez konieczności pisania kodu prologu i epilogu. Ta funkcja służy do pisania własnych sekwencji kodu prologu/epilogu przy użyciu kodu asemblera wbudowanego. Funkcji "naked" są szczególnie przydatne w pisaniu sterowniki urządzeń wirtualnych.  Należy pamiętać, że **"naked"** atrybut jest prawidłowy tylko w x86 i ARM i nie jest dostępny na [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
__declspec(naked) declarator  
```  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ **"naked"** atrybutu, dotyczy tylko definicja funkcji i nie jest modyfikatora typu, funkcji "naked" należy użyć składni atrybutów rozszerzonych i [__declspec](../cpp/declspec.md) — słowo kluczowe.  
  

 Kompilator nie może wygenerować wbudowanej funkcji dla funkcji z atrybutem "naked", nawet wtedy, gdy funkcja jest również oznaczona za pomocą [__forceinline](inline-functions-cpp.md) — słowo kluczowe.  

  
 Kompilator generuje błąd, jeśli **"naked"** atrybut jest stosowany do coś innego niż definicji metody nieczłonkowską.  
  
## <a name="examples"></a>Przykłady  
 Ten kod definiuje funkcję za pomocą **"naked"** atrybutu:  
  
```  
__declspec( naked ) int func( formal_parameters ) {}  
```  
  
 Lub też:  
  
```  
#define Naked __declspec( naked )  
Naked int func( formal_parameters ) {}  
```  
  
 **"Naked"** atrybut ma wpływ jedynie charakter generowania kodu kompilator sekwencji prologu i epilogu funkcji. Nie ma wpływu na kod, który jest generowany w przypadku wywołania tych funkcji. W efekcie **"naked"** atrybut nie jest uważany za część typu funkcji i wskaźników do funkcji nie może mieć **"naked"** atrybutu. Ponadto **"naked"** atrybutu nie można zastosować do definicji danych. Na przykład ten przykładowy kod generuje błąd:  
  
```  
__declspec( naked ) int i;  
// Error--naked attribute not permitted on data declarations.  
```  
  
 **"Naked"** atrybut ma zastosowanie tylko do definicji funkcji i nie można określić w prototypu funkcji. Na przykład tej deklaracji generuje błąd kompilatora:  
  
```  
__declspec( naked ) int func();  // Error--naked attribute not permitted on function declarations  
```  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [Wywołania funkcji Naked](../cpp/naked-function-calls.md)