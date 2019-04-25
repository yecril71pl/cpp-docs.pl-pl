---
title: Ostrzeżenie LNK4006 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4006
helpviewer_keywords:
- LNK4006
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
ms.openlocfilehash: c81c93a6df8c7eef809f243e3dc56164ea548371
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187144"
---
# <a name="linker-tools-warning-lnk4006"></a>Ostrzeżenie LNK4006 narzędzi konsolidatora

symbol jest już zdefiniowany w obiekcie; druga definicja została zignorowana

Dany `symbol`, wyświetlane w formie urządzonej, został zdefiniowany wiele razy. W przypadku tego ostrzeżenia `symbol` zostaną dodane dwa razy, ale jej pierwszy formularz, który będzie używany.

Możesz uzyskać to ostrzeżenie, jeśli próbujesz scalić dwie biblioteki importu do jednego.

Do odbudowywania biblioteki wykonawczej języka C, możesz zignorować ten komunikat.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem, korzystając z poniższymi możliwymi rozwiązaniami

1. Dany `symbol` może być funkcją spakowanych utworzone przez kompilowanie za pomocą [/Gy](../../build/reference/gy-enable-function-level-linking.md). Ten symbol został dołączony w więcej niż jeden plik, ale został zmieniony między kompilacje. Skompiluj ponownie wszystkie pliki, które obejmują `symbol`.

1. Dany `symbol` mogły być zdefiniowane inaczej w dwa obiekty Członkowskie w innych bibliotekach.

1. Bezwzględna mogły być zdefiniowane dwa razy, podając inną wartość w każdej definicji.

1. Odebranie komunikatu o błędzie podczas łączenia bibliotek `symbol` już istnieje w bibliotece, którego jest dodawany.