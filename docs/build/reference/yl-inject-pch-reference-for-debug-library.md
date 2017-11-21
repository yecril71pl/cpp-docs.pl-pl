---
title: "-Yi (Wstaw Odnośnik PCH dla bibliotek debugowania) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /yi
dev_langs: C++
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 271681849d78eb8a6a4032bcbafbcc81b96c9f9b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (Wprowadź odnośnik PCH dla bibliotek debugowania)
Używane, jeśli Tworzenie biblioteki debugowania, które używa prekompilowanych nagłówków i kompilacja zakończy się niepowodzeniem.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Ylsymbol  
```  
  
```  
/Yl-  
```  
  
## <a name="arguments"></a>Argumenty  
 `symbol`  
 Dowolne symbol ma być przechowywany w module obiektu.  
  
 \-  
 Znak minus (-), która jawnie wyłącza **/Yl** — opcja kompilatora.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie używa kompilator **/Yl** opcji (bez określania *symbol*). **/Yl** opcja umożliwia włączenie debugera uzyskać pełne informacje na temat typów. **/Yl-** wyłącza domyślne zachowanie.  
  
 Podczas kompilowania modułu z **/Yc** i **/Yl**`symbol`, kompilator tworzy symbol podobne do __ @@_PchSym\_@00@... @`symbol`, gdzie wielokropek (...) reprezentuje ciąg znaków generowanych przez konsolidator i zapisuje go w module obiektu. Każdego pliku źródłowego, który kompilacji z tym prekompilowanego nagłówka odwołuje się do określonego symbolu, co powoduje, że konsolidator, aby zawierał obiektu modułu i jego informacje o debugowaniu w bibliotece.  
  
 Ta opcja może generować LNK1211. Po określeniu [/Yc (Utwórz prekompilowany plik nagłówka)](../../build/reference/yc-create-precompiled-header-file.md) i [/z7, / zi, /ZI (Format informacji debugowania)](../../build/reference/z7-zi-zi-debug-information-format.md) opcje kompilatora tworzy plik prekompilowanego nagłówka, który zawiera informacje o debugowaniu. Błąd może wystąpić, gdy prekompilowany nagłówek są przechowywane w bibliotece, za pomocą biblioteki do tworzenia obiektu modułu oraz kod źródłowy nie odwołuje się do żadnej funkcji, który definiuje prekompilowanego pliku nagłówkowego.  
  
 Aby rozwiązać ten problem, określ **/Yl**`symbol`, gdzie `symbol` jest nazwa dowolnego symbolu w bibliotece, podczas tworzenia pliku prekompilowanego nagłówka, który nie zawiera żadnych definicji funkcji. Ta opcja nakazuje programowi kompilatora do przechowywania informacji o debugowaniu w pliku prekompilowanego nagłówka.  
  
 Aby uzyskać więcej informacji o prekompilowanych nagłówków zobacz:  
  
-   [/Y (prekompilowane nagłówki)](../../build/reference/y-precompiled-headers.md)  
  
-   [Tworzenie prekompilowanych plików nagłówka](../../build/reference/creating-precompiled-header-files.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji kompilatora w **dodatkowe opcje** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)