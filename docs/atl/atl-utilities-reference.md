---
title: "Odwołanie do narzędzi ALT | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: dd8a2888-34f4-461e-9bf4-834218f9b95b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 69f085df8b5dadbd0ba9d20596d37cb6313bb3f0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="atl-utilities-reference"></a>Odwołanie do narzędzi ALT
ATL udostępnia kod do manipulowania adresy URL i ścieżki w formie [CPathT](../atl/reference/cpatht-class.md) i [CUrl](../atl/reference/curl-class.md). Puli wątków [CThreadPool](../atl/reference/cthreadpool-class.md), mogą być używane w aplikacji. Ten kod znajduje się w atlpath.h i atlutil.h.  
  
### <a name="classes"></a>Klasy  
  
|||  
|-|-|  
|[Klasa CPathT](../atl/reference/cpatht-class.md)|Ta klasa reprezentuje ścieżkę.|  
|[Klasa CDebugReportHook](../atl/reference/cdebugreporthook-class.md)|Klasa używana do wysyłania raportów debugowania do nazwanego potoku.|  
|[Klasa CNonStatelessWorker](../atl/reference/cnonstatelessworker-class.md)|Odbiera żądania z puli wątków i przekazuje je do obiektu procesu roboczego, który zostanie utworzona i zniszczona na każdym żądaniu.|  
|[Klasa CNoWorkerThread](../atl/reference/cnoworkerthread-class.md)|Klasa jest używana jako argument dla `MonitorClass` parametr szablonu klasy pamięci podręcznej, jeśli chcesz wyłączyć konserwacji dynamiczne pamięci podręcznej.|  
|[Klasa CThreadPool](../atl/reference/cthreadpool-class.md)|Ta klasa udostępnia puli wątków roboczych, które przetwarzają kolejki elementów roboczych.|  
|[Klasa CUrl](../atl/reference/curl-class.md)|Ta klasa reprezentuje adres URL. Umożliwia manipulowania każdy element adresu URL, niezależnie od innych, czy podczas analizowania istniejący adres URL ciągu lub tworzenia ciągu od początku.|  
|[Klasa CWorkerThread](../atl/reference/cworkerthread-class.md)|Ta klasa tworzy wątku roboczego lub korzysta z jednego z istniejących, czeka na jeden lub więcej dojść obiektu jądra i wykonuje funkcję określonego klienta, gdy jeden z uchwytów zostanie zasygnalizowane.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[CPath](../atl/reference/atl-typedefs.md#cpath)|Specjalizacji [CPathT](../atl/reference/cpatht-class.md) przy użyciu `CString`.|  
|[CPathA](../atl/reference/atl-typedefs.md#cpatha)|Specjalizacji [CPathT](../atl/reference/cpatht-class.md) przy użyciu `CStringA`.|  
|[CPathW](../atl/reference/atl-typedefs.md#cpathw)|Specjalizacji [CPathT](../atl/reference/cpatht-class.md) przy użyciu `CStringW`.|  
|[ATL_URL_PORT](../atl/reference/atl-typedefs.md#atl_url_port)|Typ użyty przez [CUrl](../atl/reference/curl-class.md) służący do określania numeru portu.|  
  
### <a name="enums"></a>Wyliczenia  
  
|||  
|-|-|  
|[ATL_URL_SCHEME](../atl/reference/atl-url-scheme-enum.md)|Elementów członkowskich to wyliczenie Podaj stałe schematy zrozumiałe [CUrl](../atl/reference/curl-class.md).|  
  
### <a name="functions"></a>Funkcje  
  
|||  
|-|-|  
|[AtlCanonicalizeUrl](../atl/reference/atl-http-utility-functions.md#atlcanonicalizeurl)|Wywołaj tę funkcję, aby nadać postać kanoniczną adresowi URL, co obejmuje konwersję niebezpiecznych znaków i spacji na sekwencje unikowe.|  
|[AtlCombineUrl](../atl/reference/atl-http-utility-functions.md#atlcombineurl)|Wywołaj tę funkcję, aby połączyć podstawowy adres URL i względny adres URL w jeden kanoniczny adres URL.|  
|[AtlEscapeUrl](../atl/reference/atl-http-utility-functions.md#atlescapeurl)|Wywołaj tę funkcję, aby skonwertować wszystkie niebezpieczne znaki na sekwencje ucieczki.|  
|[AtlGetDefaultUrlPort](../atl/reference/atl-http-utility-functions.md#atlgetdefaulturlport)|Wywołanie tej funkcji można pobrać domyślny numer portu skojarzonego z określonym protokołu internetowego lub schematu.|  
|[AtlHexValue](../atl/reference/atl-text-encoding-functions.md#atlhexvalue)|Wywołaj tę funkcję, aby uzyskać wartość liczbową z liczby szesnastkowej.|  
|[AtlIsUnsafeUrlChar](../atl/reference/atl-http-utility-functions.md#atlisunsafeurlchar)|Wywołaj tę funkcję, aby się dowiedzieć, czy użycie danego znaku w adresie URL jest bezpieczne.|  
|[AtlUnescapeUrl](../atl/reference/atl-http-utility-functions.md#atlunescapeurl)|Wywołaj tę funkcję, aby skonwertować znaki przetworzone przez sekwencje ucieczki z powrotem do ich oryginalnych wartości.|  
|[SystemTimeToHttpDate](../atl/reference/atl-http-utility-functions.md#systemtimetohttpdate)|Wywołaj tę funkcję, aby skonwertować czas systemowy na ciąg znaków w formacie odpowiednim do używania nagłówków HTTP.|  

|[ATLPath::AddBackslash](../atl/reference/atl-path-functions.md#addbackslash)| Ta funkcja jest przeciążony element otoki dla [PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561). |  
|[ATLPath::AddExtension](../atl/reference/atl-path-functions.md#addextension)| Ta funkcja jest przeciążony element otoki dla [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563). |  
|[ATLPath::Append](../atl/reference/atl-path-functions.md#append)| Ta funkcja jest przeciążony element otoki dla [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565). |  
|[ATLPath::BuildRoot](../atl/reference/atl-path-functions.md#buildroot)| Ta funkcja jest przeciążony element otoki dla [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567). |  
|[ATLPath::Canonicalize](../atl/reference/atl-path-functions.md#canonicalize)| Ta funkcja jest przeciążony element otoki dla [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569). |  
|[ATLPath::Combine](../atl/reference/atl-path-functions.md#combine)| Ta funkcja jest przeciążony element otoki dla [PathCombine](http://msdn.microsoft.com/library/windows/desktop/bb773571). |  
|[ATLPath::CommonPrefix](../atl/reference/atl-path-functions.md#commonprefix)| Ta funkcja jest przeciążony element otoki dla [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574). |  
|[ATLPath::CompactPath](../atl/reference/atl-path-functions.md#compactpath)| Ta funkcja jest przeciążony element otoki dla [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575). |  
|[ATLPath::CompactPathEx](../atl/reference/atl-path-functions.md#compactpathex)| Ta funkcja jest przeciążony element otoki dla [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578). |  
|[ATLPath::FileExists](../atl/reference/atl-path-functions.md#fileexists)| Ta funkcja jest przeciążony element otoki dla [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584). |  
|[ATLPath::FindExtension](../atl/reference/atl-path-functions.md#findextension)| Ta funkcja jest przeciążony element otoki dla [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587). |  
|[ATLPath::FindFileName](../atl/reference/atl-path-functions.md#findfilename)| Ta funkcja jest przeciążony element otoki dla [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589). |  
|[ATLPath::GetDriveNumber](../atl/reference/atl-path-functions.md#getdrivenumber)| Ta funkcja jest przeciążony element otoki dla [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612). |  
|[ATLPath::IsDirectory](../atl/reference/atl-path-functions.md#isdirectory)| Ta funkcja jest przeciążony element otoki dla [PathIsDirectory](http://msdn.microsoft.com/library/windows/desktop/bb773621). |  
|[ATLPath::IsFileSpec](../atl/reference/atl-path-functions.md#isfilespec)| Ta funkcja jest przeciążony element otoki dla [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627). |  
|[ATLPath::IsPrefix](../atl/reference/atl-path-functions.md#isprefix)| Ta funkcja jest przeciążony element otoki dla [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650). |  
|[ATLPath::IsRelative](../atl/reference/atl-path-functions.md#isrelative)| Ta funkcja jest przeciążony element otoki dla [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660). |  
|[ATLPath::IsRoot](../atl/reference/atl-path-functions.md#isroot)| Ta funkcja jest przeciążony element otoki dla [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674). |  
|[ATLPath::IsSameRoot](../atl/reference/atl-path-functions.md#issameroot)| Ta funkcja jest przeciążony element otoki dla [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687). |  
|[ATLPath::IsUNC](../atl/reference/atl-path-functions.md#isunc)| Ta funkcja jest przeciążony element otoki dla [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712). |  
|[ATLPath::IsUNCServer](../atl/reference/atl-path-functions.md#isuncserver)| Ta funkcja jest przeciążony element otoki dla [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722). |  
|[ATLPath::IsUNCServerShare](../atl/reference/atl-path-functions.md#isuncservershare)| Ta funkcja jest przeciążony element otoki dla [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723). |  
|[ATLPath::MakePretty](../atl/reference/atl-path-functions.md#makepretty)| Ta funkcja jest przeciążony element otoki dla [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725). |  
|[ATLPath::MatchSpec](../atl/reference/atl-path-functions.md#matchspec)| Ta funkcja jest przeciążony element otoki dla [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727). |  
|[ATLPath::QuoteSpaces](../atl/reference/atl-path-functions.md#quotespaces)| Ta funkcja jest przeciążony element otoki dla [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739). |  
|[ATLPath::RelativePathTo](../atl/reference/atl-path-functions.md#relativepathto)| Ta funkcja jest przeciążony element otoki dla [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740). |  
|[ATLPath::RemoveArgs](../atl/reference/atl-path-functions.md#removeargs)| Ta funkcja jest przeciążony element otoki dla [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742). |  
|[ATLPath::RemoveBackslash](../atl/reference/atl-path-functions.md#removebackslash)| Ta funkcja jest przeciążony element otoki dla [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743). |  
|[ATLPath::RemoveBlanks](../atl/reference/atl-path-functions.md#removeblanks)| Ta funkcja jest przeciążony element otoki dla [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745). |  
|[ATLPath::RemoveExtension](../atl/reference/atl-path-functions.md#removeextension)| Ta funkcja jest przeciążony element otoki dla [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746). |  
|[ATLPath::RemoveFileSpec](../atl/reference/atl-path-functions.md#removefilespec)| Ta funkcja jest przeciążony element otoki dla [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748). |  
|[ATLPath::RenameExtension](../atl/reference/atl-path-functions.md#renameextension)| Ta funkcja jest przeciążony element otoki dla [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749). |  
|[ATLPath::SkipRoot](../atl/reference/atl-path-functions.md#skiproot)| Ta funkcja jest przeciążony element otoki dla [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754). |  
|[ATLPath::StripPath](../atl/reference/atl-path-functions.md#strippath)| Ta funkcja jest przeciążony element otoki dla [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756). |  
|[ATLPath::StripToRoot](../atl/reference/atl-path-functions.md#striptoroot)| Ta funkcja jest przeciążony element otoki dla [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757). |  
|[ATLPath::UnquoteSpaces](../atl/reference/atl-path-functions.md#unquotespaces)| Ta funkcja jest przeciążony element otoki dla [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763). |  
  

## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../atl/active-template-library-atl-concepts.md)   
 [Składniki ATL COM pulpitu](../atl/atl-com-desktop-components.md)
