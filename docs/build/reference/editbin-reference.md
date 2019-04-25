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
ms.openlocfilehash: 45c2967a55e85ae31bb77bb2e8d50415eafbea46
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293033"
---
# <a name="editbin-reference"></a>Odwołanie EDITBIN

Edytor plików binarnych Microsoft COFF (EDITBIN. Z rozszerzeniem EXE) modyfikuje pliki binarne Common Object File Format (COFF). Aby zmodyfikować pliki obiektów, plików wykonywalnych i bibliotek dołączanych dynamicznie (DLL), można użyć polecenia EDITBIN.

> [!NOTE]
>  To narzędzie można uruchomić tylko z poziomu wiersza polecenia programu Visual Studio. Nie można uruchomić go z wiersza poleceń systemu lub Eksploratora plików.

EDITBIN nie jest dostępna do użycia w plikach z [/GL](gl-whole-program-optimization.md) — opcja kompilatora. Wszelkie modyfikacje plików binarnych produkowanych z opcją /GL będą musieli można osiągnąć poprzez ponownej kompilacji, a następnie połączenie.

- [Wiersz polecenia EDITBIN](editbin-command-line.md)

- [Opcje polecenia EDITBIN](editbin-options.md)

## <a name="see-also"></a>Zobacz także

[MSVC dodatkowe narzędzia do kompilacji](c-cpp-build-tools.md)
