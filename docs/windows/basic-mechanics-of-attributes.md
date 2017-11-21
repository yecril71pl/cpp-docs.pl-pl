---
title: "Podstawowa mechanika atrybutów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- attributes [C++], inserting in code
- attributes [C++], about attributes
ms.assetid: dc2069c3-b9f3-4a72-965c-4e5208ce8e34
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ebf81d5bfb20f151cc8f405fb8346b66451f77e2
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="basic-mechanics-of-attributes"></a>Podstawowa mechanika atrybutów
Istnieją trzy sposoby Wstawianie atrybutów do projektu. Po pierwsze można wstawić je ręcznie do kodu źródłowego. Po drugie można wstawić je do projektu przy użyciu siatki właściwości obiektu. Na koniec można wstawić je przy użyciu różnych kreatorów. Aby uzyskać więcej informacji o korzystaniu z okna właściwości i różnych kreatorów, zobacz [tworzenie i zarządzanie projekty Visual C++](../ide/creating-and-managing-visual-cpp-projects.md).  
  
 Jako przed, gdy projekt jest budowany, kompilator analizuje każdego pliku źródłowego języka C++, tworzenie pliku obiektu. Jednak gdy kompilator napotka atrybutu, jest analizowana i składniowo zweryfikowane. Kompilator dynamicznie wywołuje dostawcy atrybutu, aby wstawić kod lub wprowadzić inne zmiany w czasie kompilacji. Implementacja dostawcy różni się w zależności od typu atrybutu. Na przykład atrybuty dotyczące ATL są implementowane przez Atlprov.dll.  
  
 Na poniższym rysunku pokazano relacji między kompilatora i dostawcy atrybutu.  
  
 ![Atrybut komunikacji](../windows/media/vccompattrcomm.gif "vcCompAttrComm")  
  
> [!NOTE]
>  Użycie atrybutu nie zmienia zawartość pliku źródłowego. Kod wygenerowany atrybutu jest widoczna tylko czas jest podczas sesji debugowania. Ponadto dla każdego pliku źródłowego w projekcie, można wygenerować pliku tekstowego, który służy do wyświetlania wyników podstawienia atrybutu. Aby uzyskać więcej informacji dotyczących tej procedury, zobacz [/Fx (scalania wstrzyknięcie kodu)](../build/reference/fx-merge-injected-code.md) i [debugowania wstrzyknięcie kodu](/visualstudio/debugger/how-to-debug-injected-code).  
  
 Jak większość konstrukcji języka C++ atrybuty mają zestaw właściwości, który definiuje ich prawidłowego użycia. To jest określany jako kontekst atrybutu i zostanie rozwiązana w tabeli atrybutu kontekstu dla każdego atrybutu odwołanie do tematu. Na przykład [coclass](../windows/coclass.md) atrybut tylko można stosować do istniejącej klasy lub struktury, w przeciwieństwie do [cpp_quote —](../windows/cpp-quote.md) atrybut, który może być wstawiony w dowolne miejsce w pliku źródłowym C++.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../windows/attributed-programming-concepts.md)