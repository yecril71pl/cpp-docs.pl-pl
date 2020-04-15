---
title: Odwołanie EDITBIN
ms.date: 11/04/2016
f1_keywords:
- editbin
helpviewer_keywords:
- binary data, editing
- object files, modifying
- EDITBIN program
- COFF files, editing
ms.assetid: efdda03b-3dfc-4d31-90e6-caf5b3977914
ms.openlocfilehash: 266347de063b4e050cb032aa2d8d74e7934b8081
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328350"
---
# <a name="editbin-reference"></a>Odwołanie EDITBIN

Edytor plików binarnych COFF firmy Microsoft (EDITBIN. EXE) modyfikuje pliki binarne Common Object File Format (COFF). Za pomocą programu EDITBIN można modyfikować pliki obiektów, pliki wykonywalne i biblioteki łączy dynamicznych (DLL).

> [!NOTE]
> To narzędzie można uruchomić tylko w wierszu polecenia programu Visual Studio. Nie można go uruchomić z wiersza polecenia systemowego lub z Eksploratora plików.

EDITBIN nie jest dostępny do użytku w plikach wyprodukowanych z opcją kompilatora [/GL.](gl-whole-program-optimization.md) Wszelkie modyfikacje plików binarnych wyprodukowanych za pomocą /GL będą musiały zostać osiągnięte poprzez ponowne komppilowanie i łączenie.

- [WIERSZ POLECENIA EDITBIN](editbin-command-line.md)

- [Opcje EDITBIN](editbin-options.md)

## <a name="see-also"></a>Zobacz też

[Dodatkowe narzędzia do budowania MSVC](c-cpp-build-tools.md)
