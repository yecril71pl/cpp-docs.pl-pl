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
ms.openlocfilehash: bd602dcde34aa7cc08486188ab5fb5925eca0eb2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081094"
---
# <a name="resource-compiler-error-rc2104"></a>Błąd kompilatora zasobów RC2104

Niezdefiniowana nazwa — słowo kluczowe lub klucz: klucz

Nie zdefiniowano określonego słowa kluczowego lub nazwę klucza.

Ten błąd jest często spowodowany przez błąd pisowni w definicji zasobu lub w pliku nagłówkowym uwzględnione. Mogą być także spowodowane przez brak pliku nagłówka.

Aby rozwiązać ten problem, Znajdź plik nagłówka, który powinien zawierać zdefiniowanych — słowo kluczowe lub nazwę klucza i sprawdź, czy jest ona objęta Twojego pliku zasobu oraz — słowo kluczowe lub klucz nazwa została wpisana poprawnie. Jeśli projekt został utworzony przy użyciu prekompilowanego nagłówka, a następnie usuń go, upewnij się, że plik zasobów nadal zawiera wszelkie wymagane nagłówki.

Aby sprawdzić określonych słów kluczowych i nazwy kluczy w pliku zasobów w programie Visual Studio, otwórz **widok zasobów** okna — na pasku menu wybierz **widoku**, **widok zasobów**— i następnie otwórz menu skrótów dla pliku .rc i wybierz polecenie **symboli zasobów** Aby wyświetlić listę zdefiniowanych symboli. Aby zmodyfikować nagłówki dołączone, otwórz menu skrótów dla pliku .rc, a następnie wybierz **zasób zawiera**.

Jeśli napotkasz ten komunikat:

```
undefined keyword or key name: MFT_STRING
```

Otwórz \MCL\MFC\Include\AfxRes.h i dodaj to dyrektywy #include:

```
#include <winresrc.h>
```