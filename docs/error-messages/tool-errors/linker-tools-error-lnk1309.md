---
title: Błąd narzędzi konsolidatora LNK1309
ms.date: 11/04/2016
f1_keywords:
- LNK1309
helpviewer_keywords:
- LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
ms.openlocfilehash: ea675ca835dfc3fe4881e5fabbea746a4442b10a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187446"
---
# <a name="linker-tools-error-lnk1309"></a>Błąd narzędzi konsolidatora LNK1309

> *type1* moduł wykrył; jest on nieprawidłowy z przełącznika/clrimagetype:*Typ2*

## <a name="remarks"></a>Uwagi

Typ obrazu CLR została zażądana przy użyciu **/clrimagetype** , ale konsolidator nie może utworzyć obrazu tego typu, ponieważ przynajmniej jeden moduł były niezgodne z tym typem.

Na przykład, jeśli określisz zostanie wyświetlone LNK1309 **Safe** i przekazać Moduł skompilowany z **/CLR: pure**.

**/CLR: pure** i **/CLR: Safe** kompilatora biblioteki opcje i pomocy technicznej są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

Jeśli użytkownik podejmie próbę tworzenie aplikacji częściowo zaufanej czystego środowiska CLR, za pomocą .lib ptrustu [d], zostanie wyświetlone LNK1309. Aby uzyskać informacje na temat tworzenia aplikacji częściowo zaufanej, zobacz [jak: Tworzenie aplikacji częściowo zaufanej przez usunięcie zależności biblioteki DLL środowiska CRT](../../dotnet/create-a-partially-trusted-application.md).

Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) i [/clrimagetype (określenie typu z obrazu CLR)](../../build/reference/clrimagetype-specify-type-of-clr-image.md).