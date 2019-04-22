---
title: Redystrybucja składników za pomocą modułów scalania
ms.date: 11/04/2016
helpviewer_keywords:
- merge modules, using
- redistributing applications, using merge modules
ms.assetid: 93b84211-bf9b-4a78-9f22-474ac2ef7840
ms.openlocfilehash: 7a110826e21f33986d68dcd46417ec5cbd5171bc
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58787554"
---
# <a name="redistributing-components-by-using-merge-modules"></a>Redystrybucja składników za pomocą modułów scalania

Program Visual Studio obejmuje [modułów scalania,](/windows/desktop/Msi/about-merge-modules) dla każdego składnika Visual C++, którego licencja pozwala na redystrybucję z aplikacją. Gdy moduł scalania jest wkompilowany w plik instalacyjny Instalatora Windows, umożliwia on wdrażanie określonych bibliotek DLL na komputerach, które mają określoną platformę. W pliku konfiguracji należy określić, że moduły scalania stanowią wymagania wstępne dotyczące aplikacji. Po zainstalowaniu programu Visual Studio, moduły scalania są zainstalowane w \Program Files\Common Files\Merge Modules\\. (Może być rozpowszechniany wyłącznie bez debugowania wersje bibliotek DLL Visual C++.) Aby uzyskać więcej informacji i łącze do listy modułów scalania, których licencja pozwala na redystrybucję, zobacz [Redistributing Visual C++ Files](redistributing-visual-cpp-files.md).

Można użyć modułów scalania, aby umożliwić instalację pakiet redystrybucyjny Visual C++ bibliotek DLL w folderze %SYSTEMROOT%\system32\. (Visual Studio używa tej techniki.) Jednakże instalacja w tym folderze się nie uda, chyba że użytkownik ma prawa administratora.

Nie zalecamy korzystania z modułów scalania z wyjątkiem przypadków, kiedy nie musisz świadczyć serwisu aplikacji i nie zależy ona od więcej niż jednej wersji biblioteki DLL. Modułów scalania dla różnych wersji tej samej biblioteki DLL nie można włączyć do jednego instalatora, moduły scalania utrudniają serwisowanie bibliotek DLL niezależnie od aplikacji. Zamiast tego zaleca się, że możesz zainstalować pakiet redystrybucyjny Visual C++.

## <a name="see-also"></a>Zobacz także

[Ponowne dystrybuowanie plików programu Visual C++](redistributing-visual-cpp-files.md)
