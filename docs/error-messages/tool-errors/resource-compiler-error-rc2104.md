---
title: Błąd kompilatora zasobów RC2104
ms.date: 11/04/2016
f1_keywords:
- RC2104
helpviewer_keywords:
- RC2104
ms.assetid: 792a3bd8-cb4c-4817-b288-4ce37082b582
ms.openlocfilehash: d4a06f88e4a73da6b711d108a1f79c14fae0907c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191642"
---
# <a name="resource-compiler-error-rc2104"></a>Błąd kompilatora zasobów RC2104

niezdefiniowane słowo kluczowe lub nazwa klucza: Key

Nie zdefiniowano określonego słowa kluczowego lub nazwy klucza.

Ten błąd jest często spowodowany literówką w definicji zasobu lub w dołączonym pliku nagłówkowym. Może być również przyczyną braku pliku nagłówkowego.

Aby rozwiązać ten problem, Znajdź plik nagłówkowy, który powinien zawierać zdefiniowane słowo kluczowe lub nazwę klucza, i sprawdź, czy jest on uwzględniony w pliku zasobów oraz czy pisownia słowa kluczowego lub nazwy klucza jest poprawna. Jeśli projekt został utworzony przy użyciu prekompilowanego nagłówka i następnie go usuniesz, upewnij się, że plik zasobów nadal zawiera wymagane nagłówki.

Aby sprawdzić zdefiniowane słowa kluczowe i nazwy kluczy w pliku zasobów, w programie Visual Studio Otwórz okno **Widok zasobów** — na pasku menu wybierz **Widok**, **Widok zasobów**— a następnie otwórz menu skrótów dla pliku. RC i wybierz pozycję **symbole zasobów** , aby wyświetlić listę zdefiniowanych symboli. Aby zmodyfikować uwzględnione nagłówki, otwórz menu skrótów dla pliku. RC, a następnie wybierz pozycję **zasób zawiera**.

Jeśli wystąpi ten komunikat:

```
undefined keyword or key name: MFT_STRING
```

Otwórz \MCL\MFC\Include\AfxRes.h i Dodaj tę dyrektywę include:

```
#include <winresrc.h>
```
