---
title: Korzystanie z kompilacji debugowania do sprawdzania nadpisywania pamięci
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
ms.openlocfilehash: 42e3a7f1f1c34ba5a263adfca7496c24e162ab5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314289"
---
# <a name="using-the-debug-build-to-check-for-memory-overwrite"></a>Korzystanie z kompilacji debugowania do sprawdzania nadpisywania pamięci

Aby użyć kompilacji debugowania do sprawdzenia zastąpienia pamięci, należy najpierw skompilować projekt w celu debugowania. Następnie przejdź do początku `InitInstance` funkcji aplikacji i Dodaj następujący wiersz:

```
afxMemDF |= checkAlwaysMemDF;
```

Program przydzielający pamięć programu Debug umieszcza w bajtach ochronę wszystkich alokacji pamięci. Jednak te bajty Guard nie wykonują żadnych dobrych, chyba że sprawdzisz, czy zostały zmienione (co wskazuje na zastępowanie pamięci). W przeciwnym razie jest to tylko bufor, który może w rzeczywistości pozwolić na zastępowanie pamięci.

Przez włączenie `checkAlwaysMemDF`, wymusimy, aby MFC wykonał wywołanie `AfxCheckMemory` funkcji za każdym razem, gdy zostanie wykonane wywołanie **New** lub **delete** . W przypadku wykrycia zastępowania pamięci zostanie wygenerowany komunikat śledzenia podobny do następującego:

```
Damage Occurred! Block=0x5533
```

Jeśli zobaczysz jeden z tych komunikatów, musisz przejść przez swój kod, aby określić, gdzie wystąpił uszkodzenie. Aby wyizolować dokładniejsze miejsce zastępowania pamięci, można wykonać jawne wywołania do `AfxCheckMemory` siebie. Przykład:

```
ASSERT(AfxCheckMemory());
    DoABunchOfStuff();
    ASSERT(AfxCheckMemory());
```

Jeśli pierwsze potwierdzenie powiedzie się, a druga nie powiedzie się, oznacza to, że zastępowanie pamięci musi wystąpić w funkcji między dwoma wywołaniami.

W zależności od charakteru aplikacji może się okazać, że program uruchamia `afxMemDF` zbyt wolno, aby testy były nawet niewolniejsze. `afxMemDF` Zmienna powoduje `AfxCheckMemory` wywoływanie dla każdego wywołania do New i DELETE. W takim przypadku należy wyrównać własne wywołania do `AfxCheckMemory`(), jak pokazano powyżej, i spróbować wyizolować zastępowanie pamięci w ten sposób.

## <a name="see-also"></a>Zobacz też

[Naprawianie problemów kompilacji wydania](fixing-release-build-problems.md)
