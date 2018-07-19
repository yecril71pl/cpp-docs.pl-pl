---
title: Jawne tworzenie wystąpienia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 834a71f5fd670874fd7dad5a77cb89a837119c2d
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940618"
---
# <a name="explicit-instantiation"></a>Jawne tworzenie wystąpienia
Jawne tworzenie wystąpienia można użyć do utworzenia wystąpienia szablonu klasy lub funkcji bez rzeczywistego używania w kodzie. Ponieważ jest to przydatne, gdy tworzysz biblioteki pliki (lib), które używają szablonów do dystrybucji, bez wystąpień szablonu definicji nie są umieszczane w plikach obiektowych (.obj).  
  
 Ten kod tworzy jawnie wystąpienie `MyStack` dla **int** zmiennych oraz sześć elementów:  
  
```cpp  
template class MyStack<int, 6>;  
```  
  
 Ta instrukcja tworzy wystąpienia `MyStack` bez zarezerwowanie magazynu dla obiektu. Kod jest generowany dla wszystkich członków.  
  
 Następny wiersz tworzy jawnie funkcja elementu członkowskiego Konstruktor:  
  
```cpp  
template MyStack<int, 6>::MyStack( void );  
```  
  
 Można jawnie utworzyć wystąpienie szablonów funkcji, przy użyciu argumentu określonego typu można ponownie zadeklarować je, jak pokazano w przykładzie w [Tworzenie wystąpienia szablonu funkcji](../cpp/function-template-instantiation.md).  
  
 Możesz użyć **extern** — słowo kluczowe, aby uniemożliwić automatyczne utworzenie wystąpienia elementów członkowskich. Na przykład:  
  
```cpp  
extern template class MyStack<int, 6>;  
```  
  
 Podobnie można oznaczyć określonych członków jako zewnętrzne i nie wystąpień:  
  
```cpp  
extern template MyStack<int, 6>::MyStack( void );  
```  
  
 Możesz użyć **extern** — słowo kluczowe, aby uniemożliwić kompilatorowi generowania tego samego kodu podczas tworzenia wystąpienia w więcej niż jeden moduł obiektu. Funkcja szablonu trzeba utworzyć przy użyciu parametrów określonego jawnego szablonu w co najmniej jeden moduł połączone, czy funkcja jest wywoływana, otrzymasz błąd konsolidatora, gdy program jest skompilowany.  
  
> [!NOTE]
>  **Extern** — słowo kluczowe w specjalizacji ma zastosowanie tylko do funkcji składowej zdefiniowanej poza treścią klasy. Funkcje zdefiniowane w obrębie deklaracji klasy są traktowane jako wbudowane funkcje i są zawsze tworzone.  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony funkcji](../cpp/function-templates.md)