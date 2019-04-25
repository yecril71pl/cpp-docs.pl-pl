---
title: Ostrzeżenie D9041 dla wiersza polecenia
ms.date: 11/04/2016
f1_keywords:
- D9041
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
ms.openlocfilehash: d9a32fbf961e980633635f277a76955a706a4b0e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62213786"
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

## <a name="see-also"></a>Zobacz także

[Błędy wiersza polecenia od D8000 do D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[Opcje kompilatora MSVC](../../build/reference/compiler-options.md)