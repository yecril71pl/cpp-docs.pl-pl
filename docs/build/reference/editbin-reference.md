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
ms.openlocfilehash: c2c0ee66ed1811755edc33b24737e057554fd01f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542912"
---
# <a name="editbin-reference"></a>Odwołanie EDITBIN

Edytor plików binarnych Microsoft COFF (EDITBIN. Z rozszerzeniem EXE) modyfikuje pliki binarne Common Object File Format (COFF). Aby zmodyfikować pliki obiektów, plików wykonywalnych i bibliotek dołączanych dynamicznie (DLL), można użyć polecenia EDITBIN.

> [!NOTE]
>  To narzędzie można uruchomić tylko z poziomu wiersza polecenia programu Visual Studio. Nie można uruchomić go z wiersza poleceń systemu lub Eksploratora plików.

EDITBIN nie jest dostępna do użycia w plikach z [/GL](../../build/reference/gl-whole-program-optimization.md) — opcja kompilatora. Wszelkie modyfikacje plików binarnych produkowanych z opcją /GL będą musieli można osiągnąć poprzez ponownej kompilacji, a następnie połączenie.

- [Wiersz polecenia EDITBIN](../../build/reference/editbin-command-line.md)

- [Opcje polecenia EDITBIN](../../build/reference/editbin-options.md)

## <a name="see-also"></a>Zobacz też

[Narzędzia kompilacji C/C++](../../build/reference/c-cpp-build-tools.md)