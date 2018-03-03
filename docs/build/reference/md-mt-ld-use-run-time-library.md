---
title: "-MT, -LD -MD, (biblioteki wykonawczej Użyj) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /ld
- /mt
- VC.Project.VCCLWCECompilerTool.RuntimeLibrary
- VC.Project.VCCLCompilerTool.RuntimeLibrary
- /md
- /ml
dev_langs:
- C++
helpviewer_keywords:
- /MT compiler option [C++]
- -MD compiler option [C++]
- threading [C++], multithread compiler option
- MSVCRTD.lib
- MSVCRT.lib
- LIBCMT.lib
- MD compiler option [C++]
- /MD compiler option [C++]
- MT compiler option [C++]
- LD compiler option [C++]
- MDd compiler option [C++]
- -MDd compiler option [C++]
- LIBCD.lib
- -MTd compiler option [C++]
- MTd compiler option [C++]
- /MTd compiler option [C++]
- -LD compiler option [C++]
- /MDd compiler option [C++]
- multithread compiler option
- _STATIC_CPPLIB symbol
- LIBC.lib
- /LD compiler option [C++]
- DLLs [C++], compiler options
- LIBCMTD.lib
- -MT compiler option [C++]
ms.assetid: cf7ed652-dc3a-49b3-aab9-ad60e5395579
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4b54a6aac55554cd7bd4698762779e540c4bc4c4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="md-mt-ld-use-run-time-library"></a>/MD, /MT, /LD (Korzystaj z bibliotek wykonawczych)
Wskazuje, czy moduł wielowątkowy jest biblioteką DLL i określa wersje biblioteki wykonawczej handlowe lub przeznaczone do debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
/MD[d]  
/MT[d]  
/LD[d]  
```  
  
## <a name="remarks"></a>Uwagi  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/ / MD**|Powoduje, że aplikacja korzysta z wersji biblioteki wykonawczej specyficznej dla wielowątkowości i specyficznej dla DLL. Definiuje `_MT` i `_DLL` i powoduje, że kompilator umieszcza nazwę biblioteki MSVCRT.lib w pliku obj.<br /><br /> Aplikacje skompilowane przy użyciu tej opcji są łączone statycznie z MSVCRT.lib. Ta biblioteka zawiera warstwę kodu, która umożliwia konsolidatorowi rozwiązywanie odwołań zewnętrznych. Rzeczywisty kod pracy jest zawarta w MSVCR*numerwersji*. Biblioteki DLL, który musi być dostępny w czasie wykonywania dla aplikacji związane z MSVCRT.lib.|  
|**/ MDd**|Definiuje `_DEBUG`, `_MT`, i `_DLL` i powoduje, że aplikacja korzysta z debugowania specyficzne dla wielowątkowej i specyficznej dla biblioteki DLL wersji biblioteki czasu wykonywania. Powoduje też, że kompilator umieszcza nazwę biblioteki MSVCRTD.lib w pliku .obj.|  
|**/ MT**|Powoduje, że aplikacja korzysta ze statycznej, wielowątkowej wersji biblioteki wykonawczej. Definiuje `_MT` i powoduje, że kompilator umieszcza nazwę biblioteki LIBCMT.lib w pliku .obj, tak aby konsolidator używał LIBCMT.lib do rozpoznawania symboli zewnętrznych.|  
|**/ MTd**|Definiuje `_DEBUG` i `_MT`. Ta opcja również powoduje, że kompilator umieszcza nazwę biblioteki LIBCMTD.lib w pliku .obj, tak aby konsolidator użył LIBCMTD.lib, aby rozwiązać zewnętrzne symbole.|  
|**/LD**|Tworzy DLL.<br /><br /> Przekazuje **/dll** opcji do konsolidatora. Konsolidator szuka, ale nie wymaga `DllMain` funkcji. Jeśli nie zapisuj `DllMain` wstawia konsolidator funkcji `DllMain` funkcja, która zwraca wartość TRUE.<br /><br /> Łączy kod uruchamiający biblioteki DLL.<br /><br /> Tworzy bibliotekę importu (.lib), jeżeli nie określono pliku eksportu (.exp) w wierszu polecenia. Bibliotekę importu łączy się z aplikacjami, które wywołują bibliotekę DLL.<br /><br /> Interpretuje [/Fe (Nazwij plik EXE)](../../build/reference/fe-name-exe-file.md) jako nazwy biblioteki DLL, zamiast pliku .exe. Domyślnie nazwa programu staje się *nazwę bazową*dll zamiast *nazwę bazową*.exe.<br /><br /> Oznacza **/MT** , chyba że zostaną jawnie określone **/ / MD**.|  
|**/ LDd**|Tworzy DLL przeznaczoną do debugowania. Definiuje `_MT` i `_DEBUG`.|  
  
 Aby uzyskać więcej informacji na temat biblioteki wykonawcze języka C i które biblioteki są używane podczas kompilacji z [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md), zobacz [Biblioteka CRT — funkcje](../../c-runtime-library/crt-library-features.md).  
  
 Wszystkie moduły przekazany do danego wywołanie konsolidator musi zostały skompilowane z tej samej opcji kompilatora biblioteki wykonawczej (**/ / MD**, **/MT**, **/LD**).  
  
 Aby uzyskać więcej informacji o sposobie używania wersje biblioteki wykonawcze debugowania, zobacz [odwołanie do biblioteki C Run-Time](../../c-runtime-library/c-run-time-library-reference.md).  
  
 Artykuł bazy wiedzy Knowledge Base Q140584 omawia też, jak wybrać odpowiednią bibliotekę wykonawczą C.  
  
 Aby uzyskać więcej informacji o bibliotekach DLL, zobacz [biblioteki dll w programie Visual C++](../../build/dlls-in-visual-cpp.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **C/C++** folderu.  
  
3.  Wybierz **generowania kodu** strony właściwości.  
  
4.  Modyfikowanie **biblioteki wykonawczej** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeLibrary%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)