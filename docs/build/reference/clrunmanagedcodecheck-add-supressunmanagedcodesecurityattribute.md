---
title: / CLRUNMANAGEDCODECHECK (Dodaj atrybut SuppressUnmanagedCodeSecurityAttribute) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRUNMANAGEDCODECHECK
dev_langs:
- C++
helpviewer_keywords:
- -CLRUNMANAGEDCODECHECK linker option
- /CLRUNMANAGEDCODECHECK linker option
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 679adc527cc70056e1292eb7e639499bd814bca6
ms.sourcegitcommit: 7838764e09819822a105accf5d773b2e37ffa0ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47429764"
---
# <a name="clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute"></a>/ CLRUNMANAGEDCODECHECK (Dodaj atrybut SuppressUnmanagedCodeSecurityAttribute)

**/ CLRUNMANAGEDCODECHECK** Określa, czy konsolidator zastosuje <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> do wygenerowanych przez konsolidator `PInvoke` wywołań z kodu zarządzanego do macierzystych bibliotek DLL.

## <a name="syntax"></a>Składnia

> **/ CLRUNMANAGEDCODECHECK**[**: NO**]

## <a name="remarks"></a>Uwagi

Domyślnie konsolidator stosuje **SuppressUnmanagedCodeSecurityAttribute** do wygenerowanych przez konsolidator `PInvoke` wywołania. Gdy **opcji/clrunmanagedcodecheck** – **SuppressUnmanagedCodeSecurityAttribute** nie ma zastosowania.

Konsolidator dodaje atrybut tylko do obiektów, które są kompilowane przy użyciu **/CLR** lub **/CLR: pure**. Jednak **/CLR: pure** — opcja kompilatora jest przestarzała w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

A `PInvoke` wywołanie jest generowany przez konsolidator, gdy konsolidator nie może odnaleźć symboli zarządzanych do zaspokojenia odwołanie z zarządzanego obiektu wywołującego, ale można znaleźć natywnych symboli do spełnienia tego odwołania. Aby uzyskać więcej informacji na temat `PInvoke`, zobacz [podczas wywoływania funkcji natywnych z kodu zarządzanego](../../dotnet/calling-native-functions-from-managed-code.md).

Należy pamiętać, że jeśli używasz <xref:System.Security.AllowPartiallyTrustedCallersAttribute> w kodzie, należy jawnie ustawić **opcji/clrunmanagedcodecheck**. Jeśli obraz zawiera atrybuty SuppressUnmanagedCodeSecurity i AllowPartiallyTrustedCallers występuje potencjalne luki w zabezpieczeniach.

Zobacz [bezpiecznego kodowania wytyczne dla niezarządzanego kodu](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code) Aby uzyskać więcej informacji na temat implikacji używania **SuppressUnmanagedCodeSecurityAttribute**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji** węzła.

1. Rozwiń **konsolidatora** węzła.

1. Wybierz **zaawansowane** stronę właściwości.

1. Modyfikowanie **CLR niezarządzanego kodu Sprawdź** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>.

## <a name="see-also"></a>Zobacz także

- [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)
- [Opcje konsolidatora](../../build/reference/linker-options.md)
