---
title: Zalecane tagi przeznaczone do komentarzy dokumentacji (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5c1b0e762ec2167a988e8e18f3dce932214716c9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="recommended-tags-for-documentation-comments-visual-c"></a>Tagi zalecane dla komentarzy do dokumentacji (Visual C++)
Kompilator Visual C++ przetworzy komentarze do dokumentacji w kodzie i tworzy plik .xdc dla każdego compiland i xdcmake.exe rozpoczyna przetwarzanie plików xdc do pliku XML. Przetwarzanie pliku XML dokumentacji jest szczegółów, który musi zostać wdrożone w lokacji.  
  
 Tagi są przetwarzane w konstrukcji, takich jak typy i elementy członkowskie typu.  
  
 Tagi musi bezpośrednio poprzedzać typów albo elementów członkowskich.  
  
> [!NOTE]
>  Komentarze dokumentacji nie można zastosować do przestrzeni nazw lub na poza definicji wiersza dla właściwości i zdarzeń; komentarze dokumentacji musi być w deklaracjach w klasie.  
  
 Kompilator będzie przetwarzać wszystkie tag, który jest prawidłowym kodem XML. Następujące tagi zawierają często używane funkcje w dokumentacji użytkownika:  
  
||||  
|-|-|-|  
|[\<c >](../ide/c-visual-cpp.md)|[\<Kod >](../ide/code-visual-cpp.md)|[\<przykład >](../ide/example-visual-cpp.md)|  
|[\<wyjątek >](../ide/exception-visual-cpp.md)1|[\<obejmują >](../ide/include-visual-cpp.md)1|[\<listy >](../ide/list-visual-cpp.md)|  
|[\<para >](../ide/para-visual-cpp.md)|[\<param >](../ide/param-visual-cpp.md)1|[\<paramref >](../ide/paramref-visual-cpp.md)1|  
|[\<uprawnienia >](../ide/permission-visual-cpp.md)1|[\<Remarks >](../ide/remarks-visual-cpp.md)|[\<Zwraca >](../ide/returns-visual-cpp.md)|  
|[\<zobacz >](../ide/see-visual-cpp.md)1|[\<SeeAlso >](../ide/seealso-visual-cpp.md)1|[\<podsumowania >](../ide/summary-visual-cpp.md)|  
|[\<wartość >](../ide/value-visual-cpp.md)|||  
  
 1. Kompilator sprawdza składnię.  
  
 W bieżącej wersji kompilatora Visual C++ nie obsługuje `<paramref>`, tag, który jest obsługiwany przez inne kompilatory Visual Studio. Visual C++ może obsługiwać `<paramref>` w przyszłej wersji.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)