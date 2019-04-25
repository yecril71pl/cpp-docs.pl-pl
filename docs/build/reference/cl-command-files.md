---
title: Pliki poleceń CL
ms.date: 11/04/2016
f1_keywords:
- cl
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
ms.openlocfilehash: 9810f7b4308eab2b47a068072039335e59e19f5f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272588"
---
# <a name="cl-command-files"></a>Pliki poleceń CL

Plik poleceń jest plik tekstowy, który zawiera opcje i nazwy plików, w przeciwnym razie należy wpisać w [wiersza polecenia](compiler-command-line-syntax.md) lub określić za pomocą [zmiennej środowiskowej CL](cl-environment-variables.md). CL przyjmuje plik polecenia kompilatora jako argument w zmiennej środowiskowej CL lub w wierszu polecenia. W przeciwieństwie do wiersza polecenia lub zmiennej środowiskowej CL, plik poleceń pozwala na używanie wielu wierszy opcji i nazw plików.

Opcje i nazwy plików w pliku poleceń są przetwarzane zgodnie z lokalizacją, nazwa_pliku polecenia, w ramach zmiennej środowiskowej CL lub w wierszu polecenia. Jeśli opcja/Link znajduje się w pliku poleceń, wszystkie opcje na pozostałą część wiersza są przekazywane do konsolidatora. Opcje w kolejnych wierszy w pliku poleceń i opcji w wierszu polecenia, po wywołaniu pliku polecenia nadal będzie akceptowane jako opcje kompilatora. Aby uzyskać więcej informacji na temat sposobu kolejność opcji ma wpływ na ich interpretacji, zobacz [kolejność opcji CL](order-of-cl-options.md).

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

## <a name="see-also"></a>Zobacz także

[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)
