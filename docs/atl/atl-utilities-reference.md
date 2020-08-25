---
title: Odwołanie do narzędzi ATL
ms.date: 11/04/2016
ms.assetid: dd8a2888-34f4-461e-9bf4-834218f9b95b
ms.openlocfilehash: f9e59a2c67d391995d94d77f526613534acb48de
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831878"
---
# <a name="atl-utilities-reference"></a>Odwołanie do narzędzi ATL

ATL zawiera kod służący do manipulowania ścieżkami i adresami URL w postaci [CPathT](../atl/reference/cpatht-class.md) i [zwinięcie](../atl/reference/curl-class.md). W aplikacjach można używać puli wątków, [CThreadPool](../atl/reference/cthreadpool-class.md). Ten kod można znaleźć w atlpath. h i atlutil. h.

## <a name="classes"></a>Klasy

| &nbsp; | &nbsp; |
|--|--|
| [Klasa CPathT](../atl/reference/cpatht-class.md) | Ta klasa reprezentuje ścieżkę. |
| [Klasa CDebugReportHook](../atl/reference/cdebugreporthook-class.md) | Użyj tej klasy, aby wysyłać raporty debugowania do nazwanego potoku. |
| [Klasa CNonStatelessWorker](../atl/reference/cnonstatelessworker-class.md) | Odbiera żądania z puli wątków i przekazuje je do obiektu procesu roboczego, który jest tworzony i niszczony dla każdego żądania. |
| [Klasa CNoWorkerThread](../atl/reference/cnoworkerthread-class.md) | Użyj tej klasy jako argumentu dla `MonitorClass` parametru szablonu do buforowania klas, jeśli chcesz wyłączyć konserwację dynamicznej pamięci podręcznej. |
| [Klasa CThreadPool](../atl/reference/cthreadpool-class.md) | Ta klasa udostępnia pulę wątków roboczych, które przetwarzają kolejkę elementów roboczych. |
| [Klasa CUrl](../atl/reference/curl-class.md) | Ta klasa reprezentuje adres URL. Pozwala ona na manipulowanie każdym elementem adresu URL niezależnie od innych, niezależnie od tego, czy jest analizowany istniejący ciąg adresu URL, czy też tworzący ciąg od podstaw. |
| [Klasa CWorkerThread](../atl/reference/cworkerthread-class.md) | Ta klasa tworzy wątek roboczy lub używa istniejącego obiektu, czeka na co najmniej jeden obiekt jądra, i wykonuje określoną funkcję klienta po zasygnalizowaniu jednego z uchwytów. |

## <a name="typedefs"></a>Typedefs

| &emsp; | &emsp; |
|--|--|
| [CPath](../atl/reference/atl-typedefs.md#cpath) | Specjalizacja [CPathT](../atl/reference/cpatht-class.md) przy użyciu `CString` . |
| [CPathA](../atl/reference/atl-typedefs.md#cpatha) | Specjalizacja [CPathT](../atl/reference/cpatht-class.md) przy użyciu `CStringA` . |
| [CPathW](../atl/reference/atl-typedefs.md#cpathw) | Specjalizacja [CPathT](../atl/reference/cpatht-class.md) przy użyciu `CStringW` . |
| [ATL_URL_PORT](../atl/reference/atl-typedefs.md#atl_url_port) | Typ używany przez [zwinięcie](../atl/reference/curl-class.md) do określenia numeru portu. |

## <a name="enums"></a>Wyliczenia

| &emsp; | &emsp; |
|--|--|
| [ATL_URL_SCHEME](../atl/reference/atl-url-scheme-enum.md) | Elementy członkowskie tego wyliczenia zapewniają stałe dla programów zrozumiałych przez [zwinięcie](../atl/reference/curl-class.md). |

## <a name="functions"></a>Functions

| &emsp; | &emsp; |
|--|--|
| [AtlCanonicalizeUrl](../atl/reference/atl-http-utility-functions.md#atlcanonicalizeurl) | Wywołaj tę funkcję, aby nadać postać kanoniczną adresowi URL, co obejmuje konwersję niebezpiecznych znaków i spacji na sekwencje unikowe. |
| [AtlCombineUrl](../atl/reference/atl-http-utility-functions.md#atlcombineurl) | Wywołaj tę funkcję, aby połączyć podstawowy adres URL i względny adres URL w jeden kanoniczny adres URL. |
| [AtlEscapeUrl](../atl/reference/atl-http-utility-functions.md#atlescapeurl) | Wywołaj tę funkcję, aby skonwertować wszystkie niebezpieczne znaki na sekwencje ucieczki. |
| [AtlGetDefaultUrlPort](../atl/reference/atl-http-utility-functions.md#atlgetdefaulturlport) | Wywołaj tę funkcję, aby uzyskać domyślny numer portu skojarzony z określonym protokołem lub schematem internetowym. |
| [AtlHexValue](../atl/reference/atl-text-encoding-functions.md#atlhexvalue) | Wywołaj tę funkcję, aby uzyskać wartość liczbową z liczby szesnastkowej. |
| [AtlIsUnsafeUrlChar](../atl/reference/atl-http-utility-functions.md#atlisunsafeurlchar) | Wywołaj tę funkcję, aby się dowiedzieć, czy użycie danego znaku w adresie URL jest bezpieczne. |
| [AtlUnescapeUrl](../atl/reference/atl-http-utility-functions.md#atlunescapeurl) | Wywołaj tę funkcję, aby skonwertować znaki przetworzone przez sekwencje ucieczki z powrotem do ich oryginalnych wartości. |
| [SystemTimeToHttpDate](../atl/reference/atl-http-utility-functions.md#systemtimetohttpdate) | Wywołaj tę funkcję, aby skonwertować czas systemowy na ciąg znaków w formacie odpowiednim do używania nagłówków HTTP. |
| [ATLPath::AddBackslash](../atl/reference/atl-path-functions.md#addbackslash) | Ta funkcja to przeciążona otoka dla elementu [PathAddBackslash] (/Windows/Desktop/API/shlwapi/NF-shlwapi-pathaddbackslasha |
| ). |
| [ATLPath:: AddExtension](../atl/reference/atl-path-functions.md#addextension) | Ta funkcja to przeciążona otoka dla [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw). |
| [ATLPath:: Append](../atl/reference/atl-path-functions.md#append) | Ta funkcja to przeciążona otoka dla [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw). |
| [ATLPath:: element buildroot](../atl/reference/atl-path-functions.md#buildroot) | Ta funkcja to przeciążona otoka dla [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw). |
| [ATLPath:: sprowadź](../atl/reference/atl-path-functions.md#canonicalize) | Ta funkcja to przeciążona otoka dla [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew). |
| [ATLPath:: Połącz](../atl/reference/atl-path-functions.md#combine) | Ta funkcja to przeciążona otoka dla [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew). |
| [ATLPath::CommonPrefix](../atl/reference/atl-path-functions.md#commonprefix) | Ta funkcja to przeciążona otoka dla [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw). |
| [ATLPath::CompactPath](../atl/reference/atl-path-functions.md#compactpath) | Ta funkcja to przeciążona otoka dla [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw). |
| [ATLPath::CompactPathEx](../atl/reference/atl-path-functions.md#compactpathex) | Ta funkcja to przeciążona otoka dla [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw). |
| [ATLPath::FileExists](../atl/reference/atl-path-functions.md#fileexists) | Ta funkcja to przeciążona otoka dla [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw). |
| [ATLPath::FindExtension](../atl/reference/atl-path-functions.md#findextension) | Ta funkcja to przeciążona otoka dla [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw). |
| [ATLPath::FindFileName](../atl/reference/atl-path-functions.md#findfilename) | Ta funkcja to przeciążona otoka dla [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew). |
| [ATLPath::GetDriveNumber](../atl/reference/atl-path-functions.md#getdrivenumber) | Ta funkcja to przeciążona otoka dla [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw). |
| [ATLPath:: IsDirectory](../atl/reference/atl-path-functions.md#isdirectory) | Ta funkcja to przeciążona otoka dla [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw). |
| [ATLPath::IsFileSpec](../atl/reference/atl-path-functions.md#isfilespec) | Ta funkcja to przeciążona otoka dla [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw). |
| [ATLPath:: IsPrefix](../atl/reference/atl-path-functions.md#isprefix) | Ta funkcja to przeciążona otoka dla [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw). |
| [ATLPath:: isrelatywn](../atl/reference/atl-path-functions.md#isrelative) | Ta funkcja to przeciążona otoka dla [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew). |
| [ATLPath:: IsRoot](../atl/reference/atl-path-functions.md#isroot) | Ta funkcja to przeciążona otoka dla [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw). |
| [ATLPath::IsSameRoot](../atl/reference/atl-path-functions.md#issameroot) | Ta funkcja to przeciążona otoka dla [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw). |
| [ATLPath::IsUNC](../atl/reference/atl-path-functions.md#isunc) | Ta funkcja to przeciążona otoka dla [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw). |
| [ATLPath::IsUNCServer](../atl/reference/atl-path-functions.md#isuncserver) | Ta funkcja to przeciążona otoka dla [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw). |
| [ATLPath::IsUNCServerShare](../atl/reference/atl-path-functions.md#isuncservershare) | Ta funkcja to przeciążona otoka dla [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew). |
| [ATLPath::MakePretty](../atl/reference/atl-path-functions.md#makepretty) | Ta funkcja to przeciążona otoka dla [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw). |
| [ATLPath::MatchSpec](../atl/reference/atl-path-functions.md#matchspec) | Ta funkcja to przeciążona otoka dla [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw). |
| [ATLPath::QuoteSpaces](../atl/reference/atl-path-functions.md#quotespaces) | Ta funkcja to przeciążona otoka dla [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw). |
| [ATLPath::RelativePathTo](../atl/reference/atl-path-functions.md#relativepathto) | Ta funkcja to przeciążona otoka dla [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow). |
| [ATLPath::RemoveArgs](../atl/reference/atl-path-functions.md#removeargs) | Ta funkcja to przeciążona otoka dla [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw). |
| [ATLPath::RemoveBackslash](../atl/reference/atl-path-functions.md#removebackslash) | Ta funkcja to przeciążona otoka dla [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw). |
| [ATLPath::RemoveBlanks](../atl/reference/atl-path-functions.md#removeblanks) | Ta funkcja to przeciążona otoka dla [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw). |
| [ATLPath::RemoveExtension](../atl/reference/atl-path-functions.md#removeextension) | Ta funkcja to przeciążona otoka dla [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw). |
| [ATLPath::RemoveFileSpec](../atl/reference/atl-path-functions.md#removefilespec) | Ta funkcja to przeciążona otoka dla [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw). |
| [ATLPath::RenameExtension](../atl/reference/atl-path-functions.md#renameextension) | Ta funkcja to przeciążona otoka dla [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw). |
| [ATLPath::SkipRoot](../atl/reference/atl-path-functions.md#skiproot) | Ta funkcja to przeciążona otoka dla [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw). |
| [ATLPath::StripPath](../atl/reference/atl-path-functions.md#strippath) | Ta funkcja to przeciążona otoka dla [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw). |
| [ATLPath::StripToRoot](../atl/reference/atl-path-functions.md#striptoroot) | Ta funkcja to przeciążona otoka dla [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw). |
| [ATLPath::UnquoteSpaces](../atl/reference/atl-path-functions.md#unquotespaces) | Ta funkcja to przeciążona otoka dla [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw). |

## <a name="see-also"></a>Zobacz też

[Pojęcia](../atl/active-template-library-atl-concepts.md)<br/>
[Składniki pulpitu COM ATL](../atl/atl-com-desktop-components.md)
