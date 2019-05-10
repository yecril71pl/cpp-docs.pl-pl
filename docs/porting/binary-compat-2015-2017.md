---
title: C++Zgodność binarną między Visual Studio 2015 i Visual Studio 2019 r.
ms.date: 05/03/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: 052874eb9273ee9a9ce1695ffdadedd9911673e1
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65449036"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2019"></a>C++Zgodność binarną między Visual Studio 2015 i Visual Studio 2019 r.

W programie Visual Studio 2013 lub starszej zgodność binarną między pliki obiektów (OBJs), biblioteki statyczne (biblioteki), dynamicznej biblioteki dll i plików wykonywalnych (exe) skompilowanych przy użyciu różnych wersji bibliotek środowiska uruchomieniowego i zestaw narzędzi kompilatora nie był gwarancji. 

W programie Visual Studio 2015 i nowszych C++ narzędzi numer główny to 14 (dla programu Visual Studio 2015 w wersji 140, wersji 141 dla programu Visual Studio 2017 i v142 dla programu Visual Studio 2019 r.). Odzwierciedla fakt, że aplikacje skompilowane z danej wersji kompilatora i biblioteki środowiska uruchomieniowego są zgodne binarne. Oznacza to, że jeśli biblioteki innej firmy, który został zbudowany przy użyciu programu Visual Studio 2015, nie trzeba ponownie go skompilować, aby można było pobrać go z aplikacji, który został utworzony za pomocą programu Visual Studio 2017 lub Visual Studio 2019 r.

Jedynym wyjątkiem od tej reguły jest to, że bibliotek statycznych lub pliki obiektów, które są kompilowane przy użyciu `/GL` przełącznika kompilatora, nie są zgodne binarnego. 

Gdy Mieszaj plików binarnych skompilowanych przy użyciu różnych obsługiwanych wersji zestaw narzędzi MSVC wizualizacji C++ zużywa do dystrybucji, że uruchomień aplikacji na nie może być starsza niż wersje zestawu narzędzi, używany do tworzenia aplikacji lub żadnych bibliotek. 

## <a name="see-also"></a>Zobacz także

[Historia zmian Visual C++](../porting/visual-cpp-change-history-2003-2015.md)
