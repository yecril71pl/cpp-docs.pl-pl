---
title: Argumenty dla metody main
ms.date: 11/04/2016
ms.assetid: 39824fef-05ad-461d-ae82-49447dda8060
ms.openlocfilehash: 918be9d281f1cb12c27c6c2f5dd834e4af137179
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313561"
---
# <a name="arguments-to-main"></a>Argumenty dla metody main

**ANSI 2.1.2.2.1** semantykę argumenty dla metody main

W Microsoft C jest wywoływana funkcja wywoływana w momencie uruchamiania programu **głównego**. Istnieje bez prototypu zadeklarowany dla **głównego**, i mogą być definiowane za pomocą zero, dwóch lub trzech parametrów:

```
int main( void )
int main( int argc, char *argv[] )
int main( int argc, char *argv[], char *envp[] )
```

Trzeci wiersz powyżej, gdzie **głównego** przyjmuje trzy parametry, to rozszerzenie Microsoft do standardu ANSI C. Trzeci parametr **envp**, jest tablicą wskaźników do zmiennych środowiskowych. **Envp** tablica jest zakończona wskaźnikiem typu null. Zobacz [funkcja main i wykonywanie programu](../c-language/main-function-and-program-execution.md) Aby uzyskać więcej informacji na temat **głównego** i **envp**.

Zmienna **argc —** nigdy nie przechowuje wartość ujemną.

Tablica ciągów kończy się **argv [argc —]**, który zawiera wskaźnik zerowy.

Wszystkie elementy **argv** tablicy są wskaźnikami do ciągów.

Wywoływane bez argumentów wiersza polecenia programu otrzyma wartość 1 dla **argc —**, jak nazwa pliku wykonywalnego jest umieszczana w **argv [0]**. (W wersjach systemu MS-DOS przed 3.0, nazwa pliku wykonywalnego nie jest dostępna. Litera "C" jest umieszczany w **argv [0]**.) Ciągi wskazywany przez **argv [1]** za pośrednictwem **argv [argc — - 1]** reprezentują parametry programu.

Parametry **argc —** i **argv** można modyfikować i zachowują swoje wartości znajdujących się w ostatniej między programów, uruchamianie i kończenie działania programu.

## <a name="see-also"></a>Zobacz także

[Środowisko](../c-language/environment.md)
