---
title: 'Instrukcje: Modyfikowanie właściwości projektu C++ i obiektów docelowych bez wprowadzania zmian w pliku projektu'
ms.date: 11/28/2018
helpviewer_keywords:
- project properties [C++], modifying outside project file
ms.openlocfilehash: ad527d8ee69a1786be7d325571f9c9ac4f9a8574
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823926"
---
# <a name="how-to-modify-c-project-properties-and-targets-without-changing-the-project-file"></a>Instrukcje: Modyfikowanie właściwości projektu C++ i obiektów docelowych bez wprowadzania zmian w pliku projektu

Bez wprowadzania zmian w pliku projektu, można zastąpić właściwości projektu i obiekty docelowe w wierszu polecenia programu MSBuild. Jest to przydatne, gdy użytkownik chce zastosować niektórych właściwości tymczasowo lub od czasu do czasu. Zakłada się pewną wiedzę na temat programu MSBuild. Aby uzyskać więcej informacji, zobacz [MSBUild](https://docs.microsoft.com/visualstudio/msbuild/msbuild).

> [!IMPORTANT]
> Aby utworzyć plik .props i .targets, można użyć edytora XML w Visual Studio lub dowolnego edytora tekstów. Nie używaj **Menedżer właściwości** w tym scenariuszu, ponieważ dodaje właściwości do pliku projektu.

*Aby zastąpić właściwości projektu:*

1. Utwórz plik .props, który określa właściwości, które chcesz zastąpić.

1. W wierszu polecenia: Ustaw ForceImportBeforeCppTargets="C:\sources\my_props.props"

*Aby zastąpić cele projektu:*

1. Tworzenie pliku .targets z ich implementacji lub określonej lokalizacji docelowej

2. W wierszu polecenia: Ustaw ForceImportAfterCppTargets = "C:\sources\my_target.targets"

Można również ustawić jedną z opcji w wierszu polecenia programu msbuild, przy użyciu opcji/p::

```cmd
> msbuild myproject.sln /p:ForceImportBeforeCppTargets="C:\sources\my_props.props"
> msbuild myproject.sln /p:ForceImportAfterCppTargets="C:\sources\my_target.targets"
```

Zastępowanie właściwości i obiektów docelowych w ten sposób jest odpowiednikiem dodając następujące instrukcje importu do wszystkich plików vcxproj w rozwiązaniu:

```cmd
<Import Project=="C:\sources\my_props.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
<Import Project==" C:\sources\my_target.targets"" />
```
