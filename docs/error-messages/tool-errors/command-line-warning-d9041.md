---
title: Ostrzeżenie D9041 dla wiersza polecenia
ms.date: 11/04/2016
f1_keywords:
- D9041
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
ms.openlocfilehash: e685e9bd0ffb58065f20f466131f8894baaf359f
ms.sourcegitcommit: 6e55aeb538b1c39af754f82d6f7738a18f5aa031
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/29/2020
ms.locfileid: "87389730"
---
# <a name="command-line-warning-d9041"></a>Ostrzeżenie D9041 dla wiersza polecenia

> Nieprawidłowa wartość "*Option-Value*" dla "/*Option-Name*"; Zakładając, że "*przyjęto wartość*"; Dodaj "/ANALYZE" do opcji wiersza poleceń podczas określania tego ostrzeżenia

Numer ostrzeżenia analizy kodu został dodany do **`/wd`** **`/we`** **`/wo`** opcji wiersza polecenia,, lub, **`/wl`** bez również określania **`/analyze`** opcji wiersza polecenia. Aby naprawić ten błąd, Dodaj **`/analyze`** opcję wiersza polecenia lub usuń nieprawidłowy numer ostrzegawczy z odpowiedniej **`/w`** opcji wiersza polecenia.

## <a name="example"></a>Przykład

Poniższy przykład wiersza polecenia generuje ostrzeżenie D9041:

```cmd
cl /EHsc /LD /wd6001 filename.cpp
```

Aby naprawić ostrzeżenie, Dodaj **`/analyze`** opcję wiersza polecenia. Jeśli **`/analyze`** nie jest obsługiwana w używanej wersji kompilatora, usuń nieprawidłowy numer ostrzegawczy z **`/wd`** opcji.

## <a name="see-also"></a>Zobacz też

[Błędy wiersza polecenia od D8000 do D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[Opcje kompilatora MSVC](../../build/reference/compiler-options.md)
