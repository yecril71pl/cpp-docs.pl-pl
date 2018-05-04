---
title: -INTEGRITYCHECK (Wymagaj sprawdzania podpisu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 997e3f5bb79ee3cbfa95c5762b0d3e998c56f362
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK (Wymagaj sprawdzania podpisu)
Określa, że podpis cyfrowy obraz binarny, muszą zostać sprawdzone w czasie ładowania.  
  
```  
/INTEGRITYCHECK[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie **/INTEGRITYCHECK** jest wyłączona.  
  
 **/INTEGRITYCHECK** opcję zestawów — nagłówek PE pliku DLL lub pliku wykonywalnego — flagi Menedżer pamięci do sprawdzenia podpisu cyfrowego w celu załadowania obrazu w systemie Windows. Ta opcja musi być ustawiona dla zarówno 32-bitowe i 64-bitowych bibliotek DLL, które implementuje kod trybu jądra załadowanych przez niektóre funkcje systemu Windows i jest zalecany dla wszystkie sterowniki urządzeń w systemie Windows Vista [!INCLUDE[win7](../../build/includes/win7_md.md)], [!INCLUDE[win8](../../build/reference/includes/win8_md.md)], [!INCLUDE[winsvr08](../../build/reference/includes/winsvr08_md.md)], i [!INCLUDE[winserver8](../../build/reference/includes/winserver8_md.md)]. Wersje systemu Windows starszych niż Windows Vista zignorować tę flagę. Aby uzyskać więcej informacji, zobacz [pliki wymuszone integralności podpisywania z przenośnego pliku wykonawczego (PE)](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx).  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzła.  
  
3.  Rozwiń węzeł **konsolidatora** węzła.  
  
4.  Wybierz **wiersza polecenia** strony właściwości.  
  
5.  W **dodatkowe opcje**, wprowadź `/INTEGRITYCHECK` lub `/INTEGRITYCHECK:NO`.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)   
 [Wymuszone pliki integralności podpisywania z przenośnym plikiem wykonawczym (PE)](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)   
 [Kod trybu jądra podpisywania wskazówki](http://msdn.microsoft.com/windows/hardware/gg487328.aspx)   
 [Biblioteki DLL AppInit w systemie Windows 7 i Windows Server 2008](http://msdn.microsoft.com/windows/hardware/gg463040.aspx)