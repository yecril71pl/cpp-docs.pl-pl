---
title: 'Strony właściwości MIDL: Zaawansowane'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCMidlTool.ErrorCheckBounds
- VC.Project.VCMidlTool.ErrorCheckStubData
- VC.Project.VCMidlTool.ErrorCheckAllocations
- VC.Project.VCMidlTool.CPreprocessOptions
- VC.Project.VCMidlTool.UndefinePreprocessorDefinitions
- VC.Project.VCMidlTool.EnableErrorChecks
- VC.Project.VCMidlTool.RedirectOutputAndErrors
- VC.Project.VCMidlTool.ErrorCheckEnumRange
- VC.Project.VCMidlTool.StructMemberAlignment
- VC.Project.VCMidlTool.ErrorCheckRefPointers
- VC.Project.VCMidlTool.ValidateParameters
helpviewer_keywords:
- MIDL, property pages
ms.assetid: d1c92e01-f403-4ed6-ab45-4043a3c9c6bb
ms.openlocfilehash: 350563d140823910667812930f9283c7640cc1ff
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823604"
---
# <a name="midl-property-pages-advanced"></a>Strony właściwości MIDL: Zaawansowane

**Zaawansowane** — strona właściwości w **MIDL** folderu określa następujące opcje kompilatora MIDL:

- Włącz sprawdzanie błędów ([/Error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Sprawdź alokacje ([/Error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Sprawdź granice ([/Error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Sprawdź zakres wartości wyliczeniowych ([/Error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Sprawdź wskaźniki odwołań ([/Error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Sprawdź dane szczątkowe ([/Error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Sprawdza poprawność parametrów ([/ robust](https://msdn.microsoft.com/library/windows/desktop/aa367363)) \*

- Wyrównanie składowej struktury ([/ZP](https://msdn.microsoft.com/library/windows/desktop/aa367388))

- Przekieruj dane wyjściowe ([/o](https://msdn.microsoft.com/library/windows/desktop/aa367351))

- Opcje przetwarzania wstępnego C ([/cpp_opt](https://msdn.microsoft.com/library/windows/desktop/aa367318))

- Usuń definicje preprocesora ([/U](https://msdn.microsoft.com/library/windows/desktop/aa367373))

\* / niezawodne jest tylko do użytku podczas kompilowania dla Windows 2000 lub nowszym maszyny. Jeśli tworzenie projektu ATL i chcesz używać / robust, zmień ten wiersz w pliku dlldatax.c:

```
#define _WIN32_WINNT 0x0400   //for Windows NT 4.0 or Windows 95 with DCOM
to
#define _WIN32_WINNT 0x0500   //for Windows NT 4.0 or Windows 95 with DCOM
```

Aby uzyskać informacje dotyczące uzyskiwania dostępu do **zaawansowane** — strona właściwości w **MIDL** folderów, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

Aby uzyskać informacje o tym, jak programowo uzyskać dostęp do MIDL opcji dla projektów języka C++, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>.

## <a name="see-also"></a>Zobacz także

[Strony właściwości MIDL](midl-property-pages.md)