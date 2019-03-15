---
title: Korzystanie z kompilacji debugowania do sprawdzania nadpisywania pamięci
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
ms.openlocfilehash: 42e3a7f1f1c34ba5a263adfca7496c24e162ab5d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823649"
---
# <a name="using-the-debug-build-to-check-for-memory-overwrite"></a>Korzystanie z kompilacji debugowania do sprawdzania nadpisywania pamięci

Aby użyć kompilacji debugowania do sprawdzania nadpisywania pamięci, należy przebudować projekt do debugowania. Następnie przejdź do początku aplikacji `InitInstance` działać, a następnie dodaj następujący wiersz:

```
afxMemDF |= checkAlwaysMemDF;
```

Debugowanie alokatora pamięci umieszcza wokół wszystkie alokacje pamięci w bajtach guard. Jednak te je przed nieprzewidzianymi bajtów nie wykonuj żadnych dobrze, należy sprawdzić, czy zostały zmienione (co oznaczałoby Zastąp pamięci). W przeciwnym razie po prostu zapewnia buforu, który może w rzeczywistości umożliwiają uzyskanie natychmiast za pomocą zastąpienia pamięci.

Dzięki włączeniu `checkAlwaysMemDF`, wymusi MFC, aby wywołać `AfxCheckMemory` funkcji każdym razem, gdy wywołanie **nowe** lub **Usuń** składa się. Zastąp pamięci zostało wykryte, wygeneruje komunikat śledzenia, który wygląda podobnie do następującego:

```
Damage Occurred! Block=0x5533
```

Jeśli zostanie wyświetlony jeden z następujących komunikatów, należy przejrzeć swój kod definiujący, w którym wystąpiło uszkodzenie. Aby wyizolować, bardziej precyzyjne, gdzie chcesz go zastąpić pamięci wystąpiło, może wykonać jawnych wywołań `AfxCheckMemory` samodzielnie. Na przykład:

```
ASSERT(AfxCheckMemory());
    DoABunchOfStuff();
    ASSERT(AfxCheckMemory());
```

Jeśli pierwszy ASSERT zakończy się pomyślnie, i drugi kończy się niepowodzeniem, oznacza to, czy chcesz go zastąpić pamięci muszą miały miejsce w funkcji między dwoma połączeniami.

W zależności od charakteru aplikacji może się okazać, że `afxMemDF` powoduje uruchamianie zbyt wolno, aby przetestować nawet przez program. `afxMemDF` Powoduje, że zmienna `AfxCheckMemory` można wywołać za każde wywołanie do nowego i usuwania. W takim przypadku należy punktowy wywołania względem `AfxCheckMemory`(), jak pokazano powyżej, a następnie spróbuj izolowania pamięć zastąpić w ten sposób.

## <a name="see-also"></a>Zobacz także

[Naprawianie problemów kompilacji wydania](fixing-release-build-problems.md)