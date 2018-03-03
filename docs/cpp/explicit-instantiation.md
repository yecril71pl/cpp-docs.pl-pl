---
title: "Jawne tworzenie wystąpienia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e272652ecc82b65d0251194f17a746ddde58fcc1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="explicit-instantiation"></a>Jawne tworzenie wystąpienia
Jawne tworzenie wystąpienia można użyć do utworzenia wystąpienia szablonu klasy lub funkcja nie jest używana w kodzie. Ponieważ jest to przydatne podczas tworzenia biblioteki plików (lib), które używają szablonów do dystrybucji, definicje szablonów bez wystąpień nie są umieszczane w plikach obiektu (.obj).  
  
 Ten kod jawnie tworzy `MyStack` dla `int` zmiennych i sześć elementów:  
  
```cpp  
template class MyStack<int, 6>;  
```  
  
 Ta instrukcja tworzy instancją typu `MyStack` bez rezerwowania dowolny magazyn dla obiekt. Kod jest generowany dla wszystkich elementów członkowskich.  
  
 Następnego wiersza tworzy jawnie funkcji członkowskiej konstruktora:  
  
```cpp  
template MyStack<int, 6>::MyStack( void );  
```  
  
 Można jawnie utworzyć wystąpienia szablonów funkcji za pomocą argumentu określonego typu można ponownie zadeklarować, jak pokazano w przykładzie w [Tworzenie wystąpienia szablonu funkcji](../cpp/function-template-instantiation.md).  
  
 Można użyć `extern` — słowo kluczowe, aby uniknąć automatycznego tworzenia wystąpień elementów członkowskich. Na przykład:  
  
```cpp  
extern template class MyStack<int, 6>;  
```  
  
 Analogicznie można oznaczyć członków określonych jako zewnętrzne i nie wystąpień:  
  
```cpp  
extern template MyStack<int, 6>::MyStack( void );  
```  
  
 Można użyć `extern` — słowo kluczowe, aby uniknąć generowania tego samego kodu podczas tworzenia wystąpienia w więcej niż jeden moduł obiektu kompilatora. Należy utworzyć wystąpienia funkcji szablonu przy użyciu parametrów określonego jawnego szablonu w co najmniej jeden moduł połączonego, jeśli funkcja jest wywoływana lub wystąpi błąd konsolidatora podczas tworzenia programu.  
  
> [!NOTE]
>  `extern` — Słowo kluczowe w specjalizacji ma zastosowanie tylko do funkcji członkowskiej zdefiniowanej poza treścią klasy. Funkcje zdefiniowane wewnątrz deklaracji klasy są traktowane jako funkcji śródwierszowych i są zawsze wystąpienia.  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony funkcji](../cpp/function-templates.md)