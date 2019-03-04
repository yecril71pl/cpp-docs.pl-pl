---
title: Odwołanie do narzędzi ALT
ms.date: 11/04/2016
ms.assetid: dd8a2888-34f4-461e-9bf4-834218f9b95b
ms.openlocfilehash: b5365ddc2924955fbdcf694065c4d4041a38eb01
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271947"
---
# <a name="atl-utilities-reference"></a>Odwołanie do narzędzi ALT

ATL zawiera kod do manipulowania ścieżek i adresów URL w postaci [CPathT](../atl/reference/cpatht-class.md) i [CUrl](../atl/reference/curl-class.md). Z puli wątków [CThreadPool](../atl/reference/cthreadpool-class.md), mogą być używane w aplikacjach. Ten kod można znaleźć w atlpath.h i atlutil.h.

### <a name="classes"></a>Klasy

|||
|-|-|
|[Klasa CPathT](../atl/reference/cpatht-class.md)|Ta klasa reprezentuje ścieżkę.|
|[Klasa CDebugReportHook](../atl/reference/cdebugreporthook-class.md)|Klasa jest używana do wysyłania raportów debugowania z nazwanym potokiem.|
|[Klasa CNonStatelessWorker](../atl/reference/cnonstatelessworker-class.md)|Odbiera żądania z puli wątków i przekazuje je do obiektu procesu roboczego, który jest tworzona i niszczona przy każdym żądaniu.|
|[Klasa CNoWorkerThread](../atl/reference/cnoworkerthread-class.md)|Klasa jest używana jako argument dla `MonitorClass` parametr szablonu klasy pamięci podręcznej, jeśli chcesz wyłączyć obsługi dynamicznej pamięci podręcznej.|
|[Klasa CThreadPool](../atl/reference/cthreadpool-class.md)|Ta klasa dostarcza puli wątków roboczych, które przetwarzają kolejki elementów roboczych.|
|[Klasa CUrl](../atl/reference/curl-class.md)|Ta klasa reprezentuje adres URL. Umożliwia on manipulowanie każdy element adresu URL, niezależnie od innych, czy analiza kodu istniejącego adresu URL ciąg lub tworzenia ciągu od podstaw.|
|[Klasa CWorkerThread](../atl/reference/cworkerthread-class.md)|Ta klasa tworzy wątek roboczy lub korzysta z istniejącą grupę, czeka na co najmniej jeden uchwytów obiektu jądra i wykonuje funkcję określonego klienta, gdy jeden z uchwytów, jest sygnalizowane.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[CPath](../atl/reference/atl-typedefs.md#cpath)|Specjalizacja [CPathT](../atl/reference/cpatht-class.md) przy użyciu `CString`.|
|[CPathA](../atl/reference/atl-typedefs.md#cpatha)|Specjalizacja [CPathT](../atl/reference/cpatht-class.md) przy użyciu `CStringA`.|
|[CPathW](../atl/reference/atl-typedefs.md#cpathw)|Specjalizacja [CPathT](../atl/reference/cpatht-class.md) przy użyciu `CStringW`.|
|[ATL_URL_PORT](../atl/reference/atl-typedefs.md#atl_url_port)|Typ używany przez [CUrl](../atl/reference/curl-class.md) do określania numeru portu.|

### <a name="enums"></a>Wyliczenia

|||
|-|-|
|[ATL_URL_SCHEME](../atl/reference/atl-url-scheme-enum.md)|Członkowie to wyliczenie zapewnia stałe dla schematów zrozumiałe [CUrl](../atl/reference/curl-class.md).|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[AtlCanonicalizeUrl](../atl/reference/atl-http-utility-functions.md#atlcanonicalizeurl)|Wywołaj tę funkcję, aby nadać postać kanoniczną adresowi URL, co obejmuje konwersję niebezpiecznych znaków i spacji na sekwencje unikowe.|
|[AtlCombineUrl](../atl/reference/atl-http-utility-functions.md#atlcombineurl)|Wywołaj tę funkcję, aby połączyć podstawowy adres URL i względny adres URL w jeden kanoniczny adres URL.|
|[AtlEscapeUrl](../atl/reference/atl-http-utility-functions.md#atlescapeurl)|Wywołaj tę funkcję, aby skonwertować wszystkie niebezpieczne znaki na sekwencje ucieczki.|
|[AtlGetDefaultUrlPort](../atl/reference/atl-http-utility-functions.md#atlgetdefaulturlport)|Wywołaj tę funkcję, aby uzyskać domyślny numer portu skojarzony z określonym protokołem lub schematem internetowym.|
|[AtlHexValue](../atl/reference/atl-text-encoding-functions.md#atlhexvalue)|Wywołaj tę funkcję, aby uzyskać wartość liczbową z liczby szesnastkowej.|
|[AtlIsUnsafeUrlChar](../atl/reference/atl-http-utility-functions.md#atlisunsafeurlchar)|Wywołaj tę funkcję, aby się dowiedzieć, czy użycie danego znaku w adresie URL jest bezpieczne.|
|[AtlUnescapeUrl](../atl/reference/atl-http-utility-functions.md#atlunescapeurl)|Wywołaj tę funkcję, aby skonwertować znaki przetworzone przez sekwencje ucieczki z powrotem do ich oryginalnych wartości.|
|[SystemTimeToHttpDate](../atl/reference/atl-http-utility-functions.md#systemtimetohttpdate)|Wywołaj tę funkcję, aby skonwertować czas systemowy na ciąg znaków w formacie odpowiednim do używania nagłówków HTTP.|

|[ATLPath::AddBackslash](../atl/reference/atl-path-functions.md#addbackslash)| Ta funkcja to przeciążona otoka dla [PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha
). | |[ ATLPath::AddExtension](../atl/reference/atl-path-functions.md#addextension)| Ta funkcja to przeciążona otoka dla [PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona). | |[ ATLPath::Append](../atl/reference/atl-path-functions.md#append)| Ta funkcja to przeciążona otoka dla [PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda). | |[ ATLPath::BuildRoot](../atl/reference/atl-path-functions.md#buildroot)| Ta funkcja to przeciążona otoka dla [PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota). | |[ ATLPath::Canonicalize](../atl/reference/atl-path-functions.md#canonicalize)| Ta funkcja to przeciążona otoka dla [PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea). | |[ ATLPath::Combine](../atl/reference/atl-path-functions.md#combine)| Ta funkcja to przeciążona otoka dla [PathCombine](/windows/desktop/api/shlwapi/nf-shlwapi-pathcombinea). | |[ ATLPath::CommonPrefix](../atl/reference/atl-path-functions.md#commonprefix)| Ta funkcja to przeciążona otoka dla [PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa). | |[ ATLPath::CompactPath](../atl/reference/atl-path-functions.md#compactpath)| Ta funkcja to przeciążona otoka dla [PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha). | |[ ATLPath::CompactPathEx](../atl/reference/atl-path-functions.md#compactpathex)| Ta funkcja to przeciążona otoka dla [PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa). | |[ ATLPath::FileExists](../atl/reference/atl-path-functions.md#fileexists)| Ta funkcja to przeciążona otoka dla [PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa). | |[ ATLPath::FindExtension](../atl/reference/atl-path-functions.md#findextension)| Ta funkcja to przeciążona otoka dla [PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona). | |[ ATLPath::FindFileName](../atl/reference/atl-path-functions.md#findfilename)| Ta funkcja to przeciążona otoka dla [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea). | |[ ATLPath::GetDriveNumber](../atl/reference/atl-path-functions.md#getdrivenumber)| Ta funkcja to przeciążona otoka dla [PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera). | |[ ATLPath::IsDirectory](../atl/reference/atl-path-functions.md#isdirectory)| Ta funkcja to przeciążona otoka dla [PathIsDirectory](/windows/desktop/api/shlwapi/nf-shlwapi-pathisdirectorya). | |[ ATLPath::IsFileSpec](../atl/reference/atl-path-functions.md#isfilespec)| Ta funkcja to przeciążona otoka dla [PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca). | |[ ATLPath::IsPrefix](../atl/reference/atl-path-functions.md#isprefix)| Ta funkcja to przeciążona otoka dla [PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa). | |[ ATLPath::IsRelative](../atl/reference/atl-path-functions.md#isrelative)| Ta funkcja to przeciążona otoka dla [PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea). | |[ ATLPath::IsRoot](../atl/reference/atl-path-functions.md#isroot)| Ta funkcja to przeciążona otoka dla [PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota). | |[ ATLPath::IsSameRoot](../atl/reference/atl-path-functions.md#issameroot)| Ta funkcja to przeciążona otoka dla [PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota). | |[ ATLPath::IsUNC](../atl/reference/atl-path-functions.md#isunc)| Ta funkcja to przeciążona otoka dla [PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca). | |[ ATLPath::IsUNCServer](../atl/reference/atl-path-functions.md#isuncserver)| Ta funkcja to przeciążona otoka dla [PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera). | |[ ATLPath::IsUNCServerShare](../atl/reference/atl-path-functions.md#isuncservershare)| Ta funkcja to przeciążona otoka dla [PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea).| |[ATLPath::MakePretty](../atl/reference/atl-path-functions.md#makepretty)|This function is an overloaded wrapper for [PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya).| |[ATLPath::MatchSpec](../atl/reference/atl-path-functions.md#matchspec)|This function is an overloaded wrapper for [PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca).| |[ATLPath::QuoteSpaces](../atl/reference/atl-path-functions.md#quotespaces)|This function is an overloaded wrapper for [PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa).| |[ATLPath::RelativePathTo](../atl/reference/atl-path-functions.md#relativepathto)|This function is an overloaded wrapper for [PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa).| |[ATLPath::RemoveArgs](../atl/reference/atl-path-functions.md#removeargs)|This function is an overloaded wrapper for [PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa).| |[ATLPath::RemoveBackslash](../atl/reference/atl-path-functions.md#removebackslash)|This function is an overloaded wrapper for [PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha).| |[ATLPath::RemoveBlanks](../atl/reference/atl-path-functions.md#removeblanks)|This function is an overloaded wrapper for [PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa).| |[ATLPath::RemoveExtension](../atl/reference/atl-path-functions.md#removeextension)|This function is an overloaded wrapper for [PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona).| |[ATLPath::RemoveFileSpec](../atl/reference/atl-path-functions.md#removefilespec)|This function is an overloaded wrapper for [PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca).| |[ATLPath::RenameExtension](../atl/reference/atl-path-functions.md#renameextension)|This function is an overloaded wrapper for [PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona).| |[ATLPath::SkipRoot](../atl/reference/atl-path-functions.md#skiproot)|This function is an overloaded wrapper for [PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota).| |[ATLPath::StripPath](../atl/reference/atl-path-functions.md#strippath)|This function is an overloaded wrapper for [PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha).| |[ATLPath::StripToRoot](../atl/reference/atl-path-functions.md#striptoroot)|This function is an overloaded wrapper for [PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota).| |[ATLPath::UnquoteSpaces](../atl/reference/atl-path-functions.md#unquotespaces)|This function is an overloaded wrapper for [PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa).|

## <a name="see-also"></a>Zobacz także

[Pojęcia](../atl/active-template-library-atl-concepts.md)<br/>
[Składniki ATL COM pulpitu](../atl/atl-com-desktop-components.md)
