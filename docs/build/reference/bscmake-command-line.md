---
title: Wiersz polecenia BSCMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, command line
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
ms.openlocfilehash: 7724069a401aadcdb2e3e8487dc85273dac357fc
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818651"
---
# <a name="bscmake-command-line"></a>Wiersz polecenia BSCMAKE

Aby uruchomić BSCMAKE, użyj następującej składni wiersza polecenia:

```
BSCMAKE [options] sbrfiles
```

Opcje mogą być wyświetlane tylko w `options` pola w wierszu polecenia.

*Sbrfiles* pole określa jeden lub więcej plików SBR, utworzony przez kompilator lub asemblera. Rozdziel nazwy plików SBR tabulacji lub spacji. Należy określić rozszerzenia. nie jest domyślnie. Można określić ścieżkę przy użyciu nazwy pliku, a następnie można użyć symboli wieloznacznych systemu operacyjnego (\* i?).

Podczas kompilacji przyrostowej można określić nowe pliki SBR, które nie były częścią oryginalnego kompilacji. Jeśli chcesz, aby wszystkie współtworzone elementy pozostaną w pliku informacyjnego przeglądarki, należy określić wszystkie pliki SBR (w tym pliki obcięte), które zostały pierwotnie użyte do utworzenia pliku .bsc. Jeżeli pominięto plik SBR wkładu tego pliku do pliku informacyjnego przeglądarki zostaną usunięte.

Nie należy określać plik SBR obcięte dla pełnej kompilacji. Pełna kompilacja wymaga wkłady wszystkich plików SBR określony. Przed wykonaniem pełnej kompilacji należy ponownie skompilować projekt i Utwórz nowy plik SBR dla każdego pliku puste.

Następujące polecenie uruchamia BSCMAKE do tworzenia pliku o nazwie MAIN.bsc z trzech plików SBR:

```
BSCMAKE main.sbr file1.sbr file2.sbr
```

Aby uzyskać powiązane informacje, zobacz [plik polecenia BSCMAKE](bscmake-command-file-response-file.md) i [opcje BSCMAKE](bscmake-options.md).

## <a name="see-also"></a>Zobacz także

[BSCMAKE — dokumentacja](bscmake-reference.md)
