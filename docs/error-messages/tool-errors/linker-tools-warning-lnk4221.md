---
title: Ostrzeżenie LNK4221 narzędzi konsolidatora
ms.date: 08/19/2019
f1_keywords:
- LNK4221
helpviewer_keywords:
- LNK4221
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
ms.openlocfilehash: 299c3ef76006b347d6770d45ca317ff0eb941ffa
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630802"
---
# <a name="linker-tools-warning-lnk4221"></a>Ostrzeżenie LNK4221 narzędzi konsolidatora

Ten plik obiektu nie definiuje żadnych wcześniej niezdefiniowanych symboli publicznych, dlatego nie będzie używany przez żadną operację konsolidacji korzystającą z tej biblioteki.

Rozważ następujące dwa fragmenty kodu.

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

Aby skompilować pliki i utworzyć dwa pliki obiektów, uruchom **cl/c a. cpp b. cpp** w wierszu polecenia. W przypadku łączenia plików obiektów przez uruchomienie **linku/lib/out: test. lib a. obj b. obj**zostanie WYŚWIETLONE ostrzeżenie LNK4221 narzędzi konsolidatora. W przypadku łączenia obiektów przez uruchomienie **linku/lib/out: test. lib b. obj a. obj**nie zostanie wyświetlone ostrzeżenie.

W drugim scenariuszu nie jest wyświetlane żadne ostrzeżenie, ponieważ konsolidator działa w sposób pierwszy-out (LIFO). W pierwszym scenariuszu b. obj jest przetwarzana przed obiektem. obj, a obiekt. obj nie ma nowych symboli do dodania. Poinstruując konsolidator, aby najpierw przetworzyć obiekt. obj, możesz uniknąć tego ostrzeżenia.

::: moniker range=">=vs-2019"

Typową przyczyną tego błędu jest to, że dwa pliki źródłowe określają opcję [/YC (Utwórz prekompilowany plik nagłówkowy)](../../build/reference/yc-create-precompiled-header-file.md) o tej samej nazwie pliku nagłówkowego określonej w polu prekompilowanego **nagłówka** . Typową przyczyną tego problemu jest usługa *PCH. h* , ponieważ domyślnie *PCH. cpp* zawiera plik *PCH. h* i nie dodaje żadnych nowych symboli. Jeśli inny plik źródłowy zawiera *PCH. h* z **/YC** i skojarzony plik. obj jest przetwarzany przed PCH. obj, konsolidator będzie generować LNK4221 narzędzi konsolidatora.

::: moniker-end

::: moniker range="<=vs-2017"

Typową przyczyną tego błędu jest to, że dwa pliki źródłowe określają opcję [/YC (Utwórz prekompilowany plik nagłówkowy)](../../build/reference/yc-create-precompiled-header-file.md) o tej samej nazwie pliku nagłówkowego określonej w polu prekompilowanego **nagłówka** . Typową przyczyną tego problemu jest *stdafx. h* , ponieważ domyślnie *stdafx. cpp* zawiera *stdafx. h* i nie dodaje żadnych nowych symboli. Jeśli inny plik źródłowy zawiera *stdafx. h* z **/YC** , a skojarzony plik. obj jest przetwarzany przed stdafx. obj, KONSOLIDATOR będzie zgłaszać LNK4221 narzędzi konsolidatora.

::: moniker-end

Jednym ze sposobów rozwiązania tego problemu jest upewnienie się, że dla każdego prekompilowanego nagłówka istnieje tylko jeden plik źródłowy, który zawiera go z **/YC**. Wszystkie inne pliki źródłowe muszą używać prekompilowanych nagłówków. Aby uzyskać więcej informacji na temat zmiany tego ustawienia, zobacz [/Yu (Użyj prekompilowanego pliku nagłówkowego)](../../build/reference/yu-use-precompiled-header-file.md).
