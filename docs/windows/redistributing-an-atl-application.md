---
title: Ponowna dystrybucja aplikacji ATL
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, redistributing
- redistributing ATL
- redistributing OLE DB templates
- OLE DB templates, redistributing
ms.assetid: 9a696b22-2345-43ec-826b-be7cb8cfd676
ms.openlocfilehash: a1da92a00d6bf88f41801f8eb99433d0c64812b1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362416"
---
# <a name="redistributing-an-atl-application"></a>Ponowna dystrybucja aplikacji ATL

Począwszy od programu Visual Studio 2012 Active Template Library (ATL) jest biblioteką tylko nagłówek. Projekt ATL nie ma dynamiczne łącze do ATL opcji. Nie biblioteki ATL jest wymagany.

Jeśli ponownie dystrybuujesz pliku wykonywalnego aplikacji biblioteki ATL, wydając polecenie należy zarejestrować plik .exe (i zawarte w niej wszystkie formanty):

```
filename /regserver
```

gdzie `filename` jest nazwą pliku wykonywalnego.

W programie Visual Studio 2010 można utworzyć Projekt ATL dla MinDependency lub konfigurację MinSize. Konfiguracja MinDependency jest właśnie te elementy otrzymasz po ustawieniu **użycie ATL** właściwości **statyczne łącze do ATL** na **ogólne** stronę właściwości i ustaw  **Biblioteka środowiska uruchomieniowego** właściwości **wielowątkowych (/ MT)** na **generowania kodu** strony właściwości (C/C++ folder).

Konfiguracja MinSize jest właśnie te elementy otrzymasz po ustawieniu **użycie ATL** właściwości **dynamiczne łącze do ATL** na **ogólne** strona właściwości lub zestawu **środowiska uruchomieniowego Biblioteka** właściwości **Multi-threaded biblioteki DLL (/ MD)** na **generowania kodu** strony właściwości (C/C++ folder).

MinSize sprawia, że dane wyjściowe pliku tak małej, jak to możliwe, ale wymaga, aby ATL100.dll i rozdystrybuować Msvcr100.dll (w przypadku wybrania **Multi-threaded biblioteki DLL (/ MD)** opcja) znajdują się na komputerze docelowym. ATL100.dll powinny być rejestrowane na komputerze docelowym, aby upewnić się, że wszystkie funkcje ATL jest obecny. ATL100.dll zawiera ANSI i eksportuje Unicode.

Jeśli tworzysz Projekt ATL lub szablony OLE DB dla elementu docelowego MinDependency, nie trzeba o zainstalowanie i zarejestrowanie ATL100.dll na komputerze docelowym, mimo że można uzyskać większy obraz programu.

Jeśli ponownie dystrybuujesz pliku wykonywalnego aplikacji biblioteki ATL, wydając polecenie należy zarejestrować plik .exe (i zawarte w niej wszystkie formanty):

```
filename /regserver
```

gdzie `filename` jest nazwą pliku wykonywalnego.

## <a name="see-also"></a>Zobacz także

[Ponowne dystrybuowanie plików programu Visual C++](redistributing-visual-cpp-files.md)
