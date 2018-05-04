---
title: -CLRUNMANAGEDCODECHECK (Dodaj SupressUnmanagedCodeSecurityAttribute) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: a00563460519225b38b1c5e745679da943d890cd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="clrunmanagedcodecheck-add-supressunmanagedcodesecurityattribute"></a>/CLRUNMANAGEDCODECHECK (Dodaj SupressUnmanagedCodeSecurityAttribute)
**/ CLRUNMANAGEDCODECHECK** Określa, czy konsolidator użyje <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> do generowanych przez konsolidator `PInvoke` wywołania z kodu zarządzanego do natywnych bibliotek DLL.  
  
## <a name="syntax"></a>Składnia  
  
```  
/CLRUNMANAGEDCODECHECK[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie konsolidator dotyczy SuppressUnmanagedCodeSecurityAttribute generowanych przez konsolidator `PInvoke` wywołania. Gdy **opcji/clrunmanagedcodecheck** obowiązuje, SuppressUnmanagedCodeSecurityAttribute nie została zastosowana.  
  
 Konsolidator dodaje atrybut tylko do obiektów, które są kompilowane przy użyciu **/CLR** lub **/CLR: pure**. Jednak **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015 i zostanie usunięta w przyszłej wersji kompilatora.  
  
 A `PInvoke` wywołanie jest generowany przez konsolidator, gdy nie można odnaleźć zarządzanego symbolu do zaspokojenia odwołania z zarządzanego wywołującego konsolidator, ale można znaleźć symbolu natywnej do spełnienia tego odwołania. Aby uzyskać więcej informacji na temat `PInvoke`, zobacz [wywoływanie funkcji natywnych z kodu zarządzanego](../../dotnet/calling-native-functions-from-managed-code.md).  
  
 Należy pamiętać, że jeśli używasz <xref:System.Security.AllowPartiallyTrustedCallersAttribute> w kodzie, należy jawnie ustawić **opcji/clrunmanagedcodecheck**. Jeśli obraz zawiera atrybuty zarówno atrybutu SuppressUnmanagedCodeSecurity i AllowPartiallyTrustedCallers jest potencjalnej luki w zabezpieczeniach.  
  
 Zobacz [Secure kodowania wytycznymi dla kodu niezarządzanego](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code) Aby uzyskać więcej informacji na temat zagadnień dotyczących używania SuppressUnmanagedCodeSecurityAttribute.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzła.  
  
3.  Rozwiń węzeł **konsolidatora** węzła.  
  
4.  Wybierz **zaawansowane** strony właściwości.  
  
5.  Modyfikowanie **CLR niezarządzany kod Sprawdź** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)