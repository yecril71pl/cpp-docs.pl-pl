---
title: Błąd narzędzi konsolidatora LNK1123 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1123
dev_langs:
- C++
helpviewer_keywords:
- LNK1123
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 482d140407a22d1ea63db07101f76f028877bdc1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206791"
---
# <a name="linker-tools-error-lnk1123"></a>Błąd narzędzi konsolidatora LNK1123

> Wystąpił błąd podczas konwersji do formatu COFF: plik jest nieprawidłowy lub uszkodzony

Pliki wejściowe musi mieć format Common Object File Format (COFF). Jeśli plik wejściowy nie jest COFF, konsolidator automatycznie podejmuje próbę przekonwertowania obiektów OMF 32-bitowego do formatu COFF lub działa na błąd. EXE w celu konwersji plików zasobów. Ten komunikat oznacza, że konsolidator nie można skonwertować pliku. Może również wystąpić podczas korzystania z niezgodną wersję narzędzia CVTRES. EXE z innej instalacji programu Visual Studio, zestaw deweloperski Windows lub .NET Framework.

> [!NOTE]
> Jeśli używasz starszej wersji programu Visual Studio automatyczna konwersja nie może być obsługiwane.

## <a name="to-fix-the-problem"></a>Aby rozwiązać ten problem

- Zastosuj wszystkie dodatki service pack i aktualizacje dla używanej wersji programu Visual Studio. Jest to szczególnie ważne w przypadku programu Visual Studio 2010.

- Spróbować utworzyć z łączeniem przyrostowym wyłączone. Na pasku menu wybierz **projektu**, **właściwości**. W **stron właściwości** okna dialogowego rozwiń **właściwości konfiguracji**, **konsolidatora**. Zmień wartość właściwości **Włącz konsolidację przyrostową** do **nie**.

- Upewnij się, że wersja narzędzia CVTRES. Znaleziono plik EXE najpierw w zmiennej środowiskowej PATH jest zgodna wersja narzędzia do kompilacji lub wersji zestawu narzędzi platformy, używaną w projekcie.

- Spróbuj wyłączyć opcję Osadzanie manifestu. Na pasku menu wybierz **projektu**, **właściwości**. W **stron właściwości** okna dialogowego rozwiń **właściwości konfiguracji**, **narzędziu manifestu**, **danych wejściowych i wyjściowych**. Zmień wartość właściwości **osadzanie manifestu** do **nie**.

- Upewnij się, że typ pliku jest prawidłowa. Na przykład upewnij się, że obiekt OMF jest 32-bitowe i nie 16-bitowych. Aby uzyskać więcej informacji, zobacz [. Pliki obj jako wejście konsolidatora](../../build/reference/dot-obj-files-as-linker-input.md) i [formatu PE](/windows/desktop/Debug/pe-format).

- Upewnij się, że plik nie jest uszkodzony. Ponownie skompiluj go, jeśli to konieczne.

## <a name="see-also"></a>Zobacz także

[Pliki .obj — wejście konsolidatora](../../build/reference/dot-obj-files-as-linker-input.md)  
[EDITBIN — dokumentacja](../../build/reference/editbin-reference.md)  
[DUMPBIN — dokumentacja](../../build/reference/dumpbin-reference.md)  
