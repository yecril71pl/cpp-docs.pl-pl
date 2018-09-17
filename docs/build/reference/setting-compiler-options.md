---
title: Ustawianie opcji kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- compiler options, setting
- cl.exe compiler, setting options
ms.assetid: 4b079f5b-0017-4124-aad6-0d2b58e427e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cf7ee185f43f62f9e9a735650801e0cbd1a1b43d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712468"
---
# <a name="setting-compiler-options"></a>Ustawianie opcji kompilatora

Opcje kompilatora C i C++ można ustawić w środowisku programistycznym lub w wierszu polecenia.

## <a name="in-the-development-environment"></a>W środowisku programistycznym

Można ustawić opcje kompilatora dla każdego projektu w jego **stron właściwości** okno dialogowe. W okienku po lewej stronie wybierz **właściwości konfiguracji**, **C/C++** , a następnie wybierz kategorię opcji kompilatora. Temat dla każdej opcji kompilatora opisuje, jak ją można ustawić i gdzie występuje w środowisku programistycznym. Zobacz [opcje kompilatora](../../build/reference/compiler-options.md) pełną listę.

## <a name="outside-the-development-environment"></a>Poza środowiskiem programistycznym

Można ustawić opcje kompilatora (CL.exe):

- [W wierszu polecenia](../../build/reference/compiler-command-line-syntax.md)

- [W plikach poleceń](../../build/reference/cl-command-files.md)

- [W zmiennej środowiskowej CL](../../build/reference/cl-environment-variables.md)

Opcje określone w zmiennej środowiskowej CL są używane za każdym razem, gdy wywołuje się CL. Jeśli plik poleceń jest podany w zmiennej środowiskowej CL lub w wierszu polecenia, używane są opcje określone w pliku poleceń. W przeciwieństwie do wiersza polecenia lub zmiennej środowiskowej CL, plik poleceń pozwala na używanie wielu wierszy opcji i nazw plików.

Opcje kompilatora są przetwarzane „od lewej do prawej,” a w przypadku wykrycia konfliktu pierwszeństwo ma ostatnia opcja (najdalej po prawej stronie). Zmienna środowiskowa CL jest przetwarzana przed wierszem polecenia, więc w każdym konflikcie między CL i wierszem polecenia ten ostatni ma pierwszeństwo.

## <a name="additional-compiler-topics"></a>Tematy dodatkowe kompilatora

- [Szybka kompilacja](../../build/reference/fast-compilation.md)

- [CL wywołuje konsolidator](../../build/reference/cl-invokes-the-linker.md)

## <a name="see-also"></a>Zobacz też

[Dokumentacja kompilacji w języku C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)