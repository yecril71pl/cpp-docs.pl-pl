---
title: "-SAFESEH (obraz ma bezpieczną obsługę wyjątków) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /SAFESEH
dev_langs: C++
helpviewer_keywords:
- /SAFESEH linker option
- -SAFESEH linker option
- SAFESEH linker option
ms.assetid: 7722ff99-b833-4c65-a855-aaca902ffcb7
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1c57a882e3a421d03b2edf97c9fb4bf2f352e5d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="safeseh-image-has-safe-exception-handlers"></a>/SAFESEH (Obraz ma bezpieczną obsługę wyjątków)
```  
/SAFESEH[:NO]  
```  
  
 Gdy **opcja/SAFESEH** jest określona, konsolidator tylko utworzenia obrazu, jeśli może utworzyć również tabelę obrazu bezpieczną obsługę wyjątków. Ta tabela określa dla systemu operacyjnego, które programy obsługi wyjątków są prawidłowe dla obrazu.  
  
 **/ SAFESEH** jest prawidłowy tylko w trakcie łączenia dla x86 elementów docelowych. **/ SAFESEH** nie jest obsługiwana dla platformy, które mają już programy obsługi wyjątków zauważyć. Na przykład na [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] i ARM wszystkie obsługi wyjątków są zapisane w PDATA. ML64.exe obsługuje dodawanie adnotacji, które emitują informację strukturalnej obsługi wyjątków (XDATA i PDATA) do obrazu, pozwalając na odpoczynek, dzięki funkcji ml64. Zobacz [MASM dla x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md) Aby uzyskać więcej informacji.  
  
 Jeśli **opcja/SAFESEH** nie zostanie określona, konsolidator utworzy obraz z tabelą programów obsługi wyjątków bezpieczne, jeśli wszystkie moduły są zgodne z funkcją bezpiecznego wyjątków. Jeśli wszystkie moduły nie były zgodne z funkcją obsługi bezpiecznych wyjątków, obraz wynikowy nie będzie zawierać tabeli obsługi bezpiecznych wyjątków. Jeśli [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) określa WINDOWSCE lub jedną z opcji EFI_ * konsolidator nie będzie próbował obrazów z tabelą programów obsługi wyjątków bezpieczne, ponieważ żadna z tych podsystemów można korzystać z informacji.  
  
 Jeśli **/SAFESEH:NO** jest określona, konsolidator nie spowoduje utworzenia obrazu z tabelą programów obsługi wyjątków bezpieczne, nawet jeśli wszystkie moduły są zgodne z bezpiecznej obsługi funkcji wyjątków.  
  
 Najczęstszą przyczyną, dla której konsolidator nie może wyprodukować obrazu, jest brak zgodności z funkcją obsługi bezpiecznych wyjątków z konsolidatorem, przez jeden lub więcej plików wejściowych (modułów). Częstą przyczyną niezgodności modułu z obsługą bezpiecznych wyjątków jest utworzenie modułu przy użyciu kompilatora poprzednich wersji programu Visual C++.  
  
 Funkcja można zarejestrować obsługi wyjątków strukturalnych, za pomocą [. SAFESEH](../../assembler/masm/dot-safeseh.md).  
  
 Nie istnieje możliwość oznaczenia istniejących danych binarnych jako posiadające obsługę wyjątków bezpiecznych (lub brak obsługi wyjątków); informację na temat obsługi wyjątków bezpiecznych muszą zostać dodane w czasie kompilacji.  
  
 Konsolidator posiada możliwość utworzenia tabeli obsługi bezpiecznych wyjątków zależnych od aplikacji przy użyciu biblioteki środowiska uruchomieniowego C. Jeśli łączysz się z [/nodefaultlib](../../build/reference/nodefaultlib-ignore-libraries.md) i chcesz uzyskać tabelę bezpieczną obsługę wyjątków, należy podać struktura konfiguracji ładowania, (na przykład można znaleźć w pliku źródłowym loadcfg.c CRT) zawierający wszystkie wpisy zdefiniowany w języku Visual C++. Na przykład:  
  
```  
#include <windows.h>  
extern DWORD_PTR __security_cookie;  /* /GS security cookie */  
  
/*  
 * The following two names are automatically created by the linker for any  
 * image that has the safe exception table present.  
*/  
  
extern PVOID __safe_se_handler_table[]; /* base of safe handler entry table */  
extern BYTE  __safe_se_handler_count;  /* absolute symbol whose address is  
                                           the count of table entries */  
typedef struct {  
    DWORD       Size;  
    DWORD       TimeDateStamp;  
    WORD        MajorVersion;  
    WORD        MinorVersion;  
    DWORD       GlobalFlagsClear;  
    DWORD       GlobalFlagsSet;  
    DWORD       CriticalSectionDefaultTimeout;  
    DWORD       DeCommitFreeBlockThreshold;  
    DWORD       DeCommitTotalFreeThreshold;  
    DWORD       LockPrefixTable;            // VA  
    DWORD       MaximumAllocationSize;  
    DWORD       VirtualMemoryThreshold;  
    DWORD       ProcessHeapFlags;  
    DWORD       ProcessAffinityMask;  
    WORD        CSDVersion;  
    WORD        Reserved1;  
    DWORD       EditList;                   // VA  
    DWORD_PTR   *SecurityCookie;  
    PVOID       *SEHandlerTable;  
    DWORD       SEHandlerCount;  
} IMAGE_LOAD_CONFIG_DIRECTORY32_2;  
  
const IMAGE_LOAD_CONFIG_DIRECTORY32_2 _load_config_used = {  
    sizeof(IMAGE_LOAD_CONFIG_DIRECTORY32_2),  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    &__security_cookie,  
    __safe_se_handler_table,  
    (DWORD)(DWORD_PTR) &__safe_se_handler_count  
};  
```  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **konsolidatora** folderu.  
  
3.  Wybierz **wiersza polecenia** strony właściwości.  
  
4.  Wybierz opcję do **dodatkowe opcje** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)