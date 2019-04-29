---
title: Błąd kompilatora zasobów RC2104
ms.date: 11/04/2016
f1_keywords:
- RC2104
helpviewer_keywords:
- RC2104
ms.assetid: 792a3bd8-cb4c-4817-b288-4ce37082b582
ms.openlocfilehash: 6ac1786e795c0c8ed57af2d341f43b8ba39229c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346564"
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