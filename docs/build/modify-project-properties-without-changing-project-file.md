---
title: 'Jak: Modyfikowanie właściwości i obiektów docelowych projektu języka C++ bez zmiany pliku projektu'
ms.date: 11/28/2018
helpviewer_keywords:
- project properties [C++], modifying outside project file
ms.openlocfilehash: 72107b572e35f222c0b03959e0edd2d23bd0130a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328459"
---
# <a name="how-to-modify-c-project-properties-and-targets-without-changing-the-project-file"></a>Jak: Modyfikowanie właściwości i obiektów docelowych projektu języka C++ bez zmiany pliku projektu

Można zastąpić właściwości projektu i obiekty docelowe z wiersza polecenia MSBuild bez zmiany pliku projektu. Jest to przydatne, gdy chcesz zastosować niektóre właściwości tymczasowo lub od czasu do czasu. Zakłada pewną wiedzę na temat MSBuild. Aby uzyskać więcej informacji, zobacz [MSBUild](https://docs.microsoft.com/visualstudio/msbuild/msbuild).

> [!IMPORTANT]
> Za pomocą Edytora XML w programie Visual Studio lub dowolnego edytora tekstu można utworzyć plik .props lub .targets. Nie należy używać **Menedżera właściwości** w tym scenariuszu, ponieważ dodaje właściwości do pliku projektu.

*Aby zastąpić właściwości projektu:*

1. Utwórz plik .props określający właściwości, które chcesz zastąpić.

1. Z wiersza polecenia: ustaw ForceImportBeforeCppTargets="C:\sources\my_props.props"

*Aby zastąpić cele projektu:*

1. Tworzenie pliku .targets z ich implementacją lub określonym celem

2. Z wiersza polecenia: ustaw ForceImportAfterCppTargets ="C:\sources\my_target.targets"

Można również ustawić jedną z opcji w wierszu polecenia msbuild za pomocą opcji /p:

```cmd
> msbuild myproject.sln /p:ForceImportBeforeCppTargets="C:\sources\my_props.props"
> msbuild myproject.sln /p:ForceImportAfterCppTargets="C:\sources\my_target.targets"
```

Zastępowanie właściwości i obiektów docelowych w ten sposób jest równoznaczne z dodawaniem następujących importów do wszystkich plików .vcxproj w rozwiązaniu:

```cmd
<Import Project=="C:\sources\my_props.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
<Import Project==" C:\sources\my_target.targets"" />
```
