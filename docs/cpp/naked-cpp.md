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
ms.openlocfilehash: 84e172c24bbb87f9243a4c0de25a98c90e043acc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="naked-c"></a>naked (C++)
**Microsoft Specific**  
  
 Dla funkcji zadeklarowana z `naked` atrybutu, kompilator generuje kod bez prolog i epilog kodu. Ta funkcja umożliwia pisanie własnych sekwencji kodu prologu/epilogu przy użyciu kodu wbudowanego asemblera. Gołe funkcje są szczególnie przydatne w pisaniu sterowniki urządzeń wirtualnych.  Należy pamiętać, że `naked` atrybut jest prawidłowy tylko w x86 i ARM i nie jest dostępny na [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
__declspec(naked) declarator  
```  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ `naked` atrybut dotyczy tylko do definicji funkcji i nie jest modyfikator typu, używania funkcji naked należy użyć składni rozszerzonych atrybutów i [__declspec](../cpp/declspec.md) — słowo kluczowe.  
  

 Kompilator nie może wygenerować wbudowanej funkcji dla funkcji oznaczone atrybutem naked, nawet wtedy, gdy funkcja jest również oznaczona atrybutem [__forceinline](inline-functions-cpp.md) — słowo kluczowe.  

  
 Kompilator generuje błąd, jeśli `naked` atrybut jest stosowany na inny niż definicję metody niebędący elementem członkowskim.  
  
## <a name="examples"></a>Przykłady  
 Ten kod definiuje funkcję z `naked` atrybutu:  
  
```  
__declspec( naked ) int func( formal_parameters ) {}  
```  
  
 Ewentualnie:  
  
```  
#define Naked __declspec( naked )  
Naked int func( formal_parameters ) {}  
```  
  
 `naked` Atrybut ma wpływ tylko rodzaj generowania kodu kompilator funkcji prolog i epilog sekwencji. Nie ma ona wpływu na kod, który zostanie wygenerowany dla wywołania funkcji. W związku z tym `naked` atrybut nie jest uznawany za część typu funkcji i nie może mieć wskaźników funkcji `naked` atrybutu. Ponadto `naked` atrybutu nie można zastosować do definicji danych. Na przykład w tym przykładowym kodzie generuje błąd:  
  
```  
__declspec( naked ) int i;       // Error--naked attribute not  
                                 // permitted on data declarations.  
```  
  
 `naked` Atrybut ma zastosowanie tylko w definicji funkcji i nie można określić w prototypu funkcji. Na przykład tej deklaracji, generuje błąd kompilatora:  
  
```  
__declspec( naked ) int func();  // Error--naked attribute not   
                                 // permitted on function declarations  
```  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [Wywołania funkcji Naked](../cpp/naked-function-calls.md)