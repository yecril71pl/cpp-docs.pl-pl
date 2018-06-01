---
title: Błąd narzędzi konsolidatora LNK1309 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1309
dev_langs:
- C++
helpviewer_keywords:
- LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ffecdc891a9fe0d1c17d6e36c87f5df10b449ec
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704101"
---
# <a name="linker-tools-error-lnk1309"></a>Błąd narzędzi konsolidatora LNK1309

> *type1* moduł wykrył; nieprawidłowy z przełączyć clrimagetype:*type2*

## <a name="remarks"></a>Uwagi

Typ obrazu CLR żądano **clrimagetype** , ale konsolidator nie może utworzyć obrazu tego typu, ponieważ co najmniej jednego modułu były niezgodne z danym typem.

Na przykład jeśli określisz zostanie wyświetlony LNK1309 **/CLRIMAGETYPE:safe** i przekaż Moduł skompilowany z **/CLR: pure**.

**/CLR: pure** i **/CLR: Safe** kompilatora biblioteki opcje i pomocy technicznej są przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r.

Widoczne będzie także LNK1309 przy próbie tworzenie aplikacji częściowo zaufanej czysty CLR, za pomocą .lib ptrustu [d]. Aby uzyskać informacje na temat tworzenia częściowo zaufanych aplikacji, zobacz [jak: utworzyć częściowo aplikacji zaufanej przez usunięcie zależności w pliku DLL biblioteki CRT](../../dotnet/create-a-partially-trusted-application.md).

Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) i [clrimagetype (określenie typu z obrazu CLR)](../../build/reference/clrimagetype-specify-type-of-clr-image.md).