---
title: Błąd kompilatora zasobów RC2104 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2104
dev_langs:
- C++
helpviewer_keywords:
- RC2104
ms.assetid: 792a3bd8-cb4c-4817-b288-4ce37082b582
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28beaad95cc33d8b014b22035f9ed641f1b6ab6d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321028"
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