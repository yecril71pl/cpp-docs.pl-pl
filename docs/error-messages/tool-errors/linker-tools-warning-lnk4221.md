---
title: Ostrzeżenie LNK4221 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4221
helpviewer_keywords:
- LNK4221
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
ms.openlocfilehash: b44ba8f0b88beda3e81d9baf59e5348ad4949b01
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460973"
---
# <a name="linker-tools-warning-lnk4221"></a>Ostrzeżenie LNK4221 narzędzi konsolidatora

Ten plik obiektu nie definiuje żadnych wcześniej niezdefiniowanych symboli publicznych, więc nie będzie można używać przez żadną operację konsolidacji, który wykorzystuje tę bibliotekę

Należy wziąć pod uwagę poniższe fragmenty kodu dwa.

```
// a.cpp
#include <atlbase.h>
```

```
// b.cpp
#include <atlbase.h>
int function()
{
   return 0;
}

```

Aby skompilować pliki i utworzyć dwa pliki obiektu, należy uruchomić **cl /c a.cpp b.cpp** polecenie w wierszu polecenia. Jeśli możesz połączyć pliki obiektów, uruchamiając **link/lib /out:test.lib a.obj b.obj**, otrzymasz ostrzeżenie LNK4221. Jeśli łączysz się obiekty, uruchamiając **link/lib /out:test.lib b.obj a.obj**, nie zostanie wyświetlone ostrzeżenie.

Ostrzeżenie nie jest generowane w drugim scenariuszu, ponieważ program łączący działa w sposób ostatni na wejściu (LIFO). W pierwszego scenariusza b.obj jest przetwarzana przed a.obj i a.obj nie ma żadnych nowych symboli do dodania. Przez poinstruowanie konsolidator, aby najpierw przetworzyć a.obj, możesz uniknąć ostrzeżenia.

Typową przyczyną tego błędu jest, gdy dwa pliki źródłowe, określ opcję [/Yc (Utwórz prekompilowany plik nagłówkowy)](../../build/reference/yc-create-precompiled-header-file.md) o tej samej nazwie pliku nagłówka, określone w **wstępnie skompilowany nagłówek** pola. Typową przyczyną tego problemu dotyczy stdafx.h, ponieważ, domyślnie zawiera stdafx.h stdafx.cpp, a nie dodaje żadnych nowych symboli. Jeśli inny plik źródłowy zawiera stdafx.h z **/Yc** i pliku .obj skojarzone jest przetwarzana przed stdafx.obj, konsolidator wygeneruje LNK4221.

Jednym sposobem, aby rozwiązać ten problem dotyczy upewnij się, że dla każdego prekompilowanego nagłówka, istnieje tylko jeden plik źródłowy, który obejmuje ją za pomocą **/Yc**. Wszystkie pliki źródłowe, należy użyć wstępnie skompilowanych nagłówków. Aby uzyskać więcej informacji na temat zmienić to ustawienie, zobacz [/Yu (Korzystaj Prekompilowanego pliku nagłówka)](../../build/reference/yu-use-precompiled-header-file.md).