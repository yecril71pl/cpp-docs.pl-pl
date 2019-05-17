---
title: / CLRUNMANAGEDCODECHECK (Usuń atrybut SuppressUnmanagedCodeSecurityAttribute)
ms.date: 05/16/2019
ms.topic: reference
f1_keywords:
- /CLRUNMANAGEDCODECHECK
helpviewer_keywords:
- -CLRUNMANAGEDCODECHECK linker option
- /CLRUNMANAGEDCODECHECK linker option
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
author: corob-msft
ms.author: corob
ms.openlocfilehash: ecc560673a8e98752289ef0e0f89d3abfc1938e4
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837242"
---
# <a name="clrunmanagedcodecheck-remove-suppressunmanagedcodesecurityattribute"></a>/ CLRUNMANAGEDCODECHECK (Usuń atrybut SuppressUnmanagedCodeSecurityAttribute)

**/ CLRUNMANAGEDCODECHECK** Określa, że konsolidator nie ma zastosowania <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> do wygenerowanych przez konsolidator `PInvoke` wywołań z kodu zarządzanego do macierzystych bibliotek DLL.

## <a name="syntax"></a>Składnia

> **/ CLRUNMANAGEDCODECHECK**[**: NO**]

## <a name="remarks"></a>Uwagi

Domyślnie konsolidator stosuje **SuppressUnmanagedCodeSecurityAttribute** do wygenerowanych przez konsolidator `PInvoke` wywołania. Gdy **opcji/clrunmanagedcodecheck** – **SuppressUnmanagedCodeSecurityAttribute** zostanie usunięty. Aby zastosować jawnie **SuppressUnmanagedCodeSecurityAttribute** do wygenerowanych przez konsolidator `PInvoke` wywołania, można użyć **/CLRUNMANAGEDCODECHECK:NO**.

Konsolidator dodaje atrybut tylko do obiektów, które są kompilowane przy użyciu **/CLR** lub **/CLR: pure**. Jednak **/CLR: pure** — opcja kompilatora jest przestarzała w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017 i nowszych wersjach.

A `PInvoke` wywołanie jest generowany przez konsolidator, gdy konsolidator nie może odnaleźć symboli zarządzanych do zaspokojenia odwołanie z zarządzanego obiektu wywołującego, ale można znaleźć natywnych symboli do spełnienia tego odwołania. Aby uzyskać więcej informacji na temat `PInvoke`, zobacz [podczas wywoływania funkcji natywnych z kodu zarządzanego](../../dotnet/calling-native-functions-from-managed-code.md).

Należy pamiętać, że jeśli używasz <xref:System.Security.AllowPartiallyTrustedCallersAttribute> w kodzie, należy jawnie ustawić **opcji/clrunmanagedcodecheck** do usunięcia **SuppressUnmanagedCodeSecurity** atrybutu. Jest potencjalne luki w zabezpieczeniach, jeśli obraz zawiera zarówno **SuppressUnmanagedCodeSecurity** i **AllowPartiallyTrustedCallers** atrybutów.

Zobacz [bezpiecznego kodowania wytyczne dla niezarządzanego kodu](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code) Aby uzyskać więcej informacji na temat implikacji używania **SuppressUnmanagedCodeSecurityAttribute**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji** węzła.

1. Rozwiń **konsolidatora** węzła.

1. Wybierz **zaawansowane** stronę właściwości.

1. Modyfikowanie **CLR niezarządzanego kodu Sprawdź** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja konsolidatora MSVC](linking.md)
- [Opcje konsolidatora MSVC](linker-options.md)
