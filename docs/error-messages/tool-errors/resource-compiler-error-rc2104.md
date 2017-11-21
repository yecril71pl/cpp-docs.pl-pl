---
title: "Błąd kompilatora zasobów RC2104 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC2104
dev_langs: C++
helpviewer_keywords: RC2104
ms.assetid: 792a3bd8-cb4c-4817-b288-4ce37082b582
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0eb2c3c7dfc8bf9a86ae8d91103fd89b30559574
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="resource-compiler-error-rc2104"></a>Błąd kompilatora zasobów RC2104
undefined — słowo kluczowe lub klucz, nazwa: klucz  
  
 Nie zdefiniowano określonej — słowo kluczowe lub nazwę klucza.  
  
 Literówka w definicji zasobu lub w pliku dołączony nagłówek często przyczyną tego błędu. Mogą być także spowodowane przez brak pliku nagłówka.  
  
 Aby rozwiązać ten problem, Znajdź plik nagłówka powinien zawierać zdefiniowanych — słowo kluczowe lub nazwę klucza i sprawdź, czy jest uwzględniona w pliku zasobów i — słowo kluczowe lub klucza nazwa została wpisana poprawnie. Jeżeli projekt został utworzony przy użyciu prekompilowanego nagłówka, a następnie usuń go, upewnij się, że plik zasobu nadal zawiera wszystkie wymagane nagłówki.  
  
 Aby sprawdzić zdefiniowanych słów kluczowych i nazwy kluczy w pliku zasobów w programie Visual Studio Otwórz **widok zasobów** okna — na pasku menu wybierz **widoku**, **widok zasobów**— i następnie otwórz plik .rc menu skrótów i wybierz polecenie **symbole zasobu** Aby wyświetlić listę zdefiniowanych symboli. Aby zmodyfikować nagłówki dołączone, otwórz plik .rc menu skrótów i wybierz **zasobów zawiera**.  
  
 Jeśli wystąpi ten komunikat:  
  
```  
undefined keyword or key name: MFT_STRING   
```  
  
 Otwórz \MCL\MFC\Include\AfxRes.h i dodaj to dyrektywy #include:  
  
```  
#include <winresrc.h>  
```