---
title: "Błąd narzędzi konsolidatora LNK1123 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1123
dev_langs:
- C++
helpviewer_keywords:
- LNK1123
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 90d46a97e27d43f97bfabd1b8ff5eab873c602a3
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="linker-tools-error-lnk1123"></a>Błąd narzędzi konsolidatora LNK1123

> Błąd podczas konwersji do formatu COFF: plik jest nieprawidłowy lub uszkodzony

Pliki wejściowe musi mieć format wspólnej obiektu pliku formatu (COFF). Jeśli plik wejściowy nie jest COFF, konsolidator automatycznie podejmuje próbę przekonwertowania obiektów OMF 32-bitowej do formatu COFF lub uruchamia CVTRES. Wywołanie pliku EXE można przekonwertować plików zasobów. Ten komunikat oznacza, że konsolidator nie można skonwertować pliku. Może to także wystąpić w przypadku korzystania z niezgodną wersję CVTRES. EXE z innej instalacji programu Visual Studio, zestaw Windows Development Kit lub .NET Framework.

> [!NOTE]
> Jeśli używasz starszej wersji programu Visual Studio nie może być obsługiwana automatycznej konwersji.

## <a name="to-fix-the-problem"></a>Aby rozwiązać ten problem

- Zastosuj wszystkie dodatki service pack i aktualizacje dla używanej wersji programu Visual Studio. Jest to szczególnie ważne dla programu Visual Studio 2010.

- Spróbuj budynku z konsolidowania przyrostowego wyłączone. Na pasku menu wybierz **projektu**, **właściwości**. W **strony właściwości** okna dialogowego rozwiń **właściwości konfiguracji**, **konsolidatora**. Zmień wartość **włączyć konsolidowania przyrostowego** do **nr**.

- Sprawdź, czy wersja CVTRES. Znaleziono EXE najpierw w zmiennej środowiskowej PATH zgodna wersja narzędzia kompilacji lub wersję zestawu narzędzi platformy, używaną w projekcie.

- Spróbuj wyłączyć opcję osadzania manifestu. Na pasku menu wybierz **projektu**, **właściwości**. W **strony właściwości** okna dialogowego rozwiń **właściwości konfiguracji**, **narzędziu manifestu**, **wejściowa i wyjściowa**. Zmień wartość **Osadź Manifest** do **nr**.

- Upewnij się, że typ pliku jest nieprawidłowa. Na przykład upewnij się, że obiekt OMF jest 32-bitowe i nie 16-bitowych. Aby uzyskać więcej informacji, zobacz [. Pliki obj jako wejście konsolidatora](../../build/reference/dot-obj-files-as-linker-input.md) i [formatu PE](https://msdn.microsoft.com/library/windows/desktop/ms680547).

- Upewnij się, że plik nie jest uszkodzony. Skompiluj ponownie, jeśli to konieczne.

## <a name="see-also"></a>Zobacz także

[Pliki .obj — wejście konsolidatora](../../build/reference/dot-obj-files-as-linker-input.md)  
[EDITBIN — dokumentacja](../../build/reference/editbin-reference.md)  
[DUMPBIN — dokumentacja](../../build/reference/dumpbin-reference.md)  
