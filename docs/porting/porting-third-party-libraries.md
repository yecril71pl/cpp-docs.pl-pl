---
title: Przenoszenie bibliotek innych firm
ms.date: 10/29/2019
helpviewer_keywords:
- 3rd-party libraries
- vspkg
ms.assetid: b055ed20-8a9e-45b2-ac2a-e3d94271c009
ms.openlocfilehash: 89460af1ad0b356f4f5952141636a9f067131750
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627191"
---
# <a name="porting-third-party-libraries"></a>Przenoszenie bibliotek innych firm

W przypadku uaktualniania projektu z programu Visual Studio 2013 lub starszej wersji programu Visual C++należy również uaktualnić wszystkie biblioteki, których używa projekt, tak aby biblioteka i projekt zostały skompilowane z tą samą wersją, jak wersja kompilatora. Jeśli nie masz dostępu do kodu źródłowego biblioteki, a biblioteka nie jest dostępna za pośrednictwem vcpkg, należy uzyskać zaktualizowany plik binarny od dostawcy biblioteki. (Aby uzyskać więcej informacji, zobacz [Omówienie potencjalnych problemów z uaktualnianiem](overview-of-potential-upgrade-issues-visual-cpp.md)).

W przypadku uaktualniania aplikacji z programu Visual Studio 2015 lub Visual Studio 2017 do programu Visual Studio 2019 nie trzeba uaktualniać zależności, ponieważ kod wygenerowany przez te trzy wersje jest zgodny z plikiem binarnym. Aby uzyskać więcej informacji, zobacz [ C++ zgodność binarna między programami Visual Studio 2015 i Visual Studio 2019](binary-compat-2015-2017.md).

## <a name="vcpkg-for-open-source-libraries"></a>vcpkg dla bibliotek Open Source

W przeszłości wyszukiwanie i uaktualnianie bibliotek innych firm było czasami nieuproszczonym zadaniem. Aby ułatwić uzyskiwanie i ponowne kompilowanie C++ bibliotek typu "open source" innych firm, C++ zespół wizualny utworzył narzędzie wiersza polecenia o nazwie **Narzędzia pakietu VC + +** lub **vcpkg**. Vcpkg ma przeszukiwany katalog wielu popularnych C++ bibliotek typu "open source". Każdą bibliotekę można zainstalować w katalogu bezpośrednio z wiersza polecenia vcpkg. Po zainstalowaniu biblioteki program Vcpkg tworzy drzewo katalogów na komputerze i dodaje plik h, lib i binarne w tym folderze. Możesz użyć tego folderu w wierszu polecenia kompilacji lub zintegrować go z Visual Studio 2015 lub nowszym za pomocą polecenia vcpkg Zintegruj install. Po zintegrowaniu lokalizacji biblioteki program Visual Studio może ją znaleźć i dodać do każdego nowo utworzonego projektu. Aby użyć biblioteki, po prostu `#include` ją, a program Visual Studio automatycznie doda ścieżkę. lib do ustawień projektu i skopiuje bibliotekę DLL do folderu rozwiązania. Aby uzyskać więcej informacji, zobacz [vcpkg: A Package Manager C++for ](../build/vcpkg.md).

## <a name="reporting-issues"></a>Raportowanie problemów

Jeśli Biblioteka open source nie jest obecna w katalogu **vcpkg** , możesz otworzyć problem w [repozytorium GitHub](https://github.com/Microsoft/vcpkg/issues) , w którym społeczność i zespół wizualny C++ mogą go zobaczyć i potencjalnie utworzyć plik portu dla tej biblioteki.

## <a name="see-also"></a>Zobacz także

[Przewodnik po przenoszeniu i uaktualnianiu pakietu Visual C++](visual-cpp-porting-and-upgrading-guide.md)
