---
title: Ostrzeżenie D9041 dla wiersza polecenia
ms.date: 11/04/2016
f1_keywords:
- D9041
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
ms.openlocfilehash: 2311c61c4d661d58302308f06b08971f94cdacab
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816311"
---
# <a name="command-line-warning-d9041"></a>Ostrzeżenie D9041 dla wiersza polecenia

Nieprawidłowa wartość 'value' dla '/ opcja'; Zakładając, że 'value'; Dodaj "/ analyze" do opcji wiersza poleceń podczas określania tego ostrzeżenia

Numer ostrzeżenia analizy kodu została dodana do **/wd**, **/we**, **/wo**, lub **/wl** opcji wiersza polecenia bez jednoczesnego określenia **/ analyze** opcji wiersza polecenia. Aby rozwiązać ten błąd, Dodaj **/ analyze** wiersza polecenia lub usuń nieprawidłowy numer ostrzeżenia z odpowiednią **Wn** opcji wiersza polecenia.

## <a name="example"></a>Przykład

Poniższy przykład wiersza polecenia generuje ostrzeżenie D9041:

```
cl /EHsc /LD /wd6001 filename.cpp
```

Aby usunąć to ostrzeżenie, należy dodać **/ analyze** opcji wiersza polecenia. Jeśli **/ analyze** jest nieobsługiwane w wersji kompilatora, usuń nieprawidłowy numer ostrzeżenia z **/wd** opcji.

## <a name="see-also"></a>Zobacz też

[Błędy wiersza polecenia od D8000 do D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[MSVC Compiler Options](../../build/reference/compiler-options.md)