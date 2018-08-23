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
ms.openlocfilehash: 5a10594391b0f3be490608f7dfa006b0c32aa2e0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609283"
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK (Wymagaj sprawdzania podpisu)
Określa, czy podpis cyfrowy obrazu binarnego musi być zaznaczone w czasie ładowania.  
  
```  
/INTEGRITYCHECK[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie **/INTEGRITYCHECK** jest wyłączona.  
  
 **/INTEGRITYCHECK** zestawy opcji — w nagłówku PE pliku DLL lub pliku wykonywalnego — Flaga, dla Menedżera pamięci sprawdzić podpis cyfrowy w celu załadowania obrazu w Windows. Ta opcja musi być ustawiona dla 32-bitowych i 64-bitowych bibliotek DLL, które implementują kod trybu jądra ładowany przez niektóre funkcje Windows i jest zalecana dla wszystkich sterowników urządzeń w Windows Vista, Windows 7, Windows 8, Windows Server 2008 i Windows Server 2012. Wersje Windows przed Windows Vista, ignorują tę flagę. Aby uzyskać więcej informacji, zobacz [wymuszone podpisywanie integralności z przenośny plik wykonywalny () plików PE](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx).  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio  
  
1.  Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń **właściwości konfiguracji** węzła.  
  
3.  Rozwiń **konsolidatora** węzła.  
  
4.  Wybierz **wiersza polecenia** stronę właściwości.  
  
5.  W **dodatkowe opcje**, wprowadź `/INTEGRITYCHECK` lub `/INTEGRITYCHECK:NO`.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)   
 [Wymuszone podpisywanie integralności z przenośny plik wykonywalny () plików PE](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)   
 [Podpisywanie instruktażu kodu trybu jądra](http://msdn.microsoft.com/windows/hardware/gg487328.aspx)   
 [AppInit dll w Windows 7 i Windows Server 2008](http://msdn.microsoft.com/windows/hardware/gg463040.aspx)