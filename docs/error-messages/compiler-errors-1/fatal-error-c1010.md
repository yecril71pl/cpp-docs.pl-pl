---
title: Błąd krytyczny C1010
ms.date: 09/03/2019
f1_keywords:
- C1010
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
ms.openlocfilehash: 40a2828ce6b21384ec49c371f23e506d816f1284
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204792"
---
# <a name="fatal-error-c1010"></a>Błąd krytyczny C1010

> nieoczekiwany koniec pliku podczas wyszukiwania prekompilowanego nagłówka. Czy zapomnisz dodać "#include *name*" do źródła?

## <a name="remarks"></a>Uwagi

Plik dołączany określony przez [/Yu](../../build/reference/yu-use-precompiled-header-file.md) nie znajduje się w pliku źródłowym. Ta opcja jest domyślnie włączona w wielu typach projektów programu C++ Visual Studio. Domyślny plik dołączania określony przez tę opcję to *PCH. h*lub *stdafx. h* w programie Visual Studio 2017 i jego wcześniejszych wersjach.

W środowisku programu Visual Studio Użyj jednej z następujących metod, aby rozwiązać ten problem:

- Upewnij się, że plik nagłówkowy *PCH. h* ani plik źródłowy *PCH. cpp* nie został przypadkowo usunięty, nie zmieniono jego nazwy ani nie został usunięty z bieżącego projektu. (W starszych projektach te pliki mogą mieć nazwę *stdafx. h* i *stdafx. cpp*).

- Upewnij się, że plik nagłówka *PCH. h* lub *stdafx. h* jest zawarty przed wszelkimi innymi dyrektywami kodu lub preprocesora w plikach źródłowych. (W programie Visual Studio ten plik nagłówkowy jest określony przez **prekompilowaną właściwość projektu pliku nagłówkowego** ).

- Można wyłączyć użycie prekompilowanego nagłówka. Wyłączenie prekompilowanych nagłówków może poważnie wpłynąć na wydajność kompilacji.

### <a name="to-turn-off-precompiled-headers"></a>Aby wyłączyć prekompilowane nagłówki

Aby wyłączyć użycie prekompilowanego nagłówka w projekcie, wykonaj następujące kroki:

1. W oknie **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy nazwę projektu, a następnie wybierz polecenie **Właściwości** , aby otworzyć okno dialogowe **strony właściwości** projektu.

1. Z listy rozwijanej **Konfiguracja** wybierz pozycję **wszystkie konfiguracje**.

1. Wybierz **Właściwości konfiguracji** > stronie właściwości **prekompilowane nagłówki** **C/C++**  > .

1. Na liście właściwości wybierz listę rozwijaną dla właściwości **prekompilowanego nagłówka** , a następnie wybierz opcję **nie używa prekompilowanych nagłówków**. Wybierz **przycisk OK** , aby zapisać zmiany.

1. W oknie **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy plik źródłowy *PCH. cpp* w projekcie. (W starszych projektach plik może mieć nazwę *stdafx. cpp*). Wybierz opcję **Wyklucz z projektu** , aby usunąć go z kompilacji.

1. Użyj menu **kompiluj** > **Wyczyść rozwiązanie** dla każdej kompilacji, którą tworzysz, aby usunąć wszystkie pliki *Project_Name. PCH* z pośrednich katalogów kompilacji.

## <a name="see-also"></a>Zobacz też

[Prekompilowane pliki nagłówkowe](../../build/creating-precompiled-header-files.md)\
[/YC (Utwórz prekompilowany plik nagłówkowy)](../../build/reference/yc-create-precompiled-header-file.md)\
[/Yu (Użyj prekompilowanego pliku nagłówkowego)](../../build/reference/yu-use-precompiled-header-file.md)
