---
title: Ostrzeżenie D9041 dla wiersza polecenia
ms.date: 11/04/2016
f1_keywords:
- D9041
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
ms.openlocfilehash: 7c685a1ca3195ad4ab52bab8b5d32b1a51534b24
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196578"
---
# <a name="command-line-warning-d9041"></a>Ostrzeżenie D9041 dla wiersza polecenia

Nieprawidłowa wartość "value" dla "Option"; przyjęto "value"; Dodaj "/ANALYZE" do opcji wiersza poleceń podczas określania tego ostrzeżenia

Numer ostrzeżenia analizy kodu został dodany do opcji wiersza polecenia **/WD**, **/we**, **/wo**lub **/WL** bez również określania opcji wiersza polecenia **/analyze** . Aby naprawić ten błąd, Dodaj opcję wiersza polecenia **/analyze** lub usuń nieprawidłowy numer ostrzegawczy z odpowiedniej opcji wiersza polecenia **/w** .

## <a name="example"></a>Przykład

Poniższy przykład wiersza polecenia generuje ostrzeżenie D9041:

```
cl /EHsc /LD /wd6001 filename.cpp
```

Aby naprawić ostrzeżenie, Dodaj opcję wiersza polecenia **/analyze** . Jeśli **/analyze** nie jest obsługiwany w używanej wersji kompilatora, usuń nieprawidłowy numer ostrzegawczy z opcji **/WD** .

## <a name="see-also"></a>Zobacz też

[Błędy wiersza polecenia od D8000 do D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[Opcje kompilatora MSVC](../../build/reference/compiler-options.md)
