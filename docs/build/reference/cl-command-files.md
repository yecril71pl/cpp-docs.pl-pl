---
title: Pliki poleceń CL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8458462304a9b739c61997505724d21bb56763f6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708674"
---
# <a name="cl-command-files"></a>Pliki poleceń CL

Plik poleceń jest plik tekstowy, który zawiera opcje i nazwy plików, w przeciwnym razie należy wpisać w [wiersza polecenia](../../build/reference/compiler-command-line-syntax.md) lub określić za pomocą [zmiennej środowiskowej CL](../../build/reference/cl-environment-variables.md). CL przyjmuje plik polecenia kompilatora jako argument w zmiennej środowiskowej CL lub w wierszu polecenia. W przeciwieństwie do wiersza polecenia lub zmiennej środowiskowej CL, plik poleceń pozwala na używanie wielu wierszy opcji i nazw plików.

Opcje i nazwy plików w pliku poleceń są przetwarzane zgodnie z lokalizacją, nazwa_pliku polecenia, w ramach zmiennej środowiskowej CL lub w wierszu polecenia. Jeśli opcja/Link znajduje się w pliku poleceń, wszystkie opcje na pozostałą część wiersza są przekazywane do konsolidatora. Opcje w kolejnych wierszy w pliku poleceń i opcji w wierszu polecenia, po wywołaniu pliku polecenia nadal będzie akceptowane jako opcje kompilatora. Aby uzyskać więcej informacji na temat sposobu kolejność opcji ma wpływ na ich interpretacji, zobacz [kolejność opcji CL](../../build/reference/order-of-cl-options.md).

Plik poleceń nie może zawierać polecenia CL. Każda opcja musi rozpoczynać się i kończyć na tym samym wierszu; Nie można użyć ukośnika odwrotnego (**\\**) połączyć opcję między dwoma wierszami.

Plik poleceń jest określona przez znak (**\@**) następuje filename; Nazwa pliku można określić ścieżkę bezwzględną lub względną.

Jeśli na przykład następujące polecenie znajduje się w pliku o nazwie Odp.:

```
/Og /link LIBC.LIB
```

i podaj polecenie CL:

```
CL /Ob2 @RESP MYAPP.C
```

polecenie, aby CL jest następująca:

```
CL /Ob2 /Og MYAPP.C /link LIBC.LIB
```

Należy pamiętać, efektywnie połączone w wierszu polecenia i polecenia w pliku poleceń.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)