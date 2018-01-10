---
title: '-Zc: wchar_t (wchar_t jest typem natywnym) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType
- VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType
- /Zc:wchar_t
dev_langs: C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- wchar_t type
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3375e39120fdc8f2b0d8d5502aa6def997511ff5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t (wchar_t jest typem natywnym)
Przeanalizować `wchar_t` jako typ wbudowany zgodnie z C++ standard. Domyślnie **/Zc:** znajduje się na.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Zc:wchar_t[-]  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli **/Zc:** , `wchar_t` mapowany na typ macierzysty specyficzne dla firmy Microsoft `__wchar_t`. Jeśli **/Zc:wchar_t-** (ze znakiem minus) jest określona, `wchar_t` mapuje `typedef` dla `unsigned short`. (W programie Visual C++ 6.0 i starszych `wchar_t` nie została zaimplementowana jako typ wbudowany, ale został zadeklarowany w wchar.h jako `typedef` dla `unsigned short`.) Nie zaleca się **/Zc:wchar_t-** ponieważ C++ standard wymaga, aby `wchar_t` być typem wbudowanym. Przy użyciu `typedef` wersji może spowodować problemy z przenośnością. Jeśli uaktualnienie z wcześniejszych wersji programu Visual C++ i wystąpi błąd kompilatora [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) ponieważ kod jest w trakcie niejawnie przekonwertować `wchar_t` do `unsigned short`, firma Microsoft zaleca, aby zmienić kod, aby naprawić błąd, zamiast tego ustawienia **/Zc:wchar_t-**.  
  
 Implementuje Microsoft `wchar_t` jako wartość bez znaku dwubajtowego. Aby uzyskać więcej informacji na temat `wchar_t`, zobacz [zakresy typu danych](../../cpp/data-type-ranges.md) i [podstawowych typów](../../cpp/fundamental-types-cpp.md).  
  
 Podczas pisania nowy kod, który ma na potrzeby współdziałania z starszego kodu, który nadal używa `typedef` wersji `wchar_t`, możesz podać przeciążenia dla obu `unsigned short` i `__wchar_t` zmian `wchar_t`, dzięki czemu kod może być połączony z kodu skompilowanego z **/Zc:** lub kodu skompilowanego bez niego. W przeciwnym razie trzeba podać tworzy dwie różne biblioteki — z, a drugi bez **/Zc:** włączone. Nawet w tym przypadku zaleca się kompilowanie starszego kodu za pomocą tego samego kompilatora, którego używa się do kompilowania nowego kodu. Nigdy nie mieszaj plików binarnych skompilowanych różnymi kompilatorami.  
  
 Gdy **/Zc:** jest określony, **_wchar_t_defined —** i **_native_wchar_t_defined —** zdefiniowanych symboli. Aby uzyskać więcej informacji, zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md).  
  
 Jeśli kod wykorzystuje funkcje globalne kompilatora COM, ponieważ **/Zc:** jest teraz na domyślnie, zaleca się zmianę jawnego odwołania do comsupp.lib—from [komentarz pragma](../../preprocessor/comment-c-cpp.md) lub polecenie wiersz — comsuppw.lib lub comsuppwd.lib. (Jeśli należy skompilować z **/Zc:wchar_t-**, użyj comsupp.lib.) Jeśli dołączasz plik nagłówkowy comdef.h, odpowiednia biblioteka jest określana automatycznie. Informacje na temat kompilatora COM obsługi, zobacz [obsługi modelu COM kompilatora](../../cpp/compiler-com-support.md).  
  
 `wchar_t` Typ nie jest obsługiwany podczas kompilowania kodu C. Aby uzyskać więcej informacji na temat problemów zgodności z programem Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  W okienku po lewej stronie rozwiń **właściwości konfiguracji**, **C/C++**, a następnie wybierz **języka**.  
  
3.  Modyfikowanie **Traktuj wchar_t jako typ wbudowany** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [/Zc (zgodność)](../../build/reference/zc-conformance.md)