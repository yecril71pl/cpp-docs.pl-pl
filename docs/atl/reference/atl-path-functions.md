---
title: "Funkcje ATL ścieżka | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ATL, path
f1_keywords:
- ATLPATH/ATL::ATLPath::AddBackslash
- ATLPATH/ATL::ATLPath::AddExtension
- ATLPATH/ATL::ATLPath::Append
- ATLPATH/ATL::ATLPath::BuildRoot
- ATLPATH/ATL::ATLPath::Canonicalize
- ATLPATH/ATL::ATLPath::Combine
- ATLPATH/ATL::ATLPath::CommonPrefix
- ATLPATH/ATL::ATLPath::CompactPath
- ATLPATH/ATL::ATLPath::CompactPathEx
- ATLPATH/ATL::ATLPath::FileExists
- ATLPATH/ATL::ATLPath::FindExtension
- ATLPATH/ATL::ATLPath::FindFileName
- ATLPATH/ATL::ATLPath::GetDriveNumber
- ATLPATH/ATL::ATLPath::IsDirectory
- ATLPATH/ATL::ATLPath::IsFileSpec
- ATLPATH/ATL::ATLPath::IsPrefix
- ATLPATH/ATL::ATLPath::IsRelative
- ATLPATH/ATL::ATLPath::IsRoot
- ATLPATH/ATL::ATLPath::IsSameRoot
- ATLPATH/ATL::ATLPath::IsUNC
- ATLPATH/ATL::ATLPath::IsUNCServer
- ATLPATH/ATL::ATLPath::IsUNCServerShare
- ATLPATH/ATL::ATLPath::MakePretty
- ATLPATH/ATL::ATLPath::MatchSpec
- ATLPATH/ATL::ATLPath::QuoteSpaces
- ATLPATH/ATL::ATLPath::RelativePathTo
- ATLPATH/ATL::ATLPath::RemoveArgs
- ATLPATH/ATL::ATLPath::RemoveBackslash
- ATLPATH/ATL::ATLPath::RemoveBlanks
- ATLPATH/ATL::ATLPath::RemoveExtension
- ATLPATH/ATL::ATLPath::RemoveFileSpec
- ATLPATH/ATL::ATLPath::RenameExtension
- ATLPATH/ATL::ATLPath::SkipRoot
- ATLPATH/ATL::ATLPath::StripPath
- ATLPATH/ATL::ATLPath::StripToRoot
- ATLPATH/ATL::ATLPath::UnquoteSpaces
ms.assetid: d1ec2b8d-7ec7-43ea-90dd-0a740d2a742b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9fa9795af90e28b2c021b179876a9f69609c7884
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2018
---
# <a name="atl-path-functions"></a>Funkcje ścieżki ATL

ATL udostępnia klasę ATLPath do manipulowania ścieżek w formie [CPathT](cpatht-class.md). Ten kod znajduje się w atlpath.h.  
  
### <a name="related-classes"></a>Klasy pokrewne  
  
|||  
|-|-|  
|[Klasa CPathT](cpatht-class.md)|Ta klasa reprezentuje ścieżkę.|  

### <a name="related-typedefs"></a>Powiązane definicje typów  
  
|||  
|-|-|  
|`CPath`|Specjalizacji [CPathT](cpatht-class.md) przy użyciu `CString`.|  
|`CPathA`|Specjalizacji [CPathT](cpatht-class.md) przy użyciu `CStringA`.|  
|`CPathW`|Specjalizacji [CPathT](cpatht-class.md) przy użyciu `CStringW`.|  
  
### <a name="functions"></a>Funkcje  
  
|||  
|-|-|  
|[ATLPath::AddBackslash](#addbackslash)|Ta funkcja jest przeciążony element otoki dla [PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561).|  
|[ATLPath::AddExtension](#addextension)|Ta funkcja jest przeciążony element otoki dla [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563).|  
|[ATLPath::Append](#append)|Ta funkcja jest przeciążony element otoki dla [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565).|  
|[ATLPath::BuildRoot](#buildroot)|Ta funkcja jest przeciążony element otoki dla [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567).|  
|[ATLPath::Canonicalize](#canonicalize)|Ta funkcja jest przeciążony element otoki dla [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569).|  
|[ATLPath::Combine](#combine)|Ta funkcja jest przeciążony element otoki dla [PathCombine](http://msdn.microsoft.com/library/windows/desktop/bb773571).|  
|[ATLPath::CommonPrefix](#commonprefix)|Ta funkcja jest przeciążony element otoki dla [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574).|  
|[ATLPath::CompactPath](#compactpath)|Ta funkcja jest przeciążony element otoki dla [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575).|  
|[ATLPath::CompactPathEx](#compactpathex)|Ta funkcja jest przeciążony element otoki dla [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578).|  
|[ATLPath::FileExists](#fileexists)|Ta funkcja jest przeciążony element otoki dla [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584).|  
|[ATLPath::FindExtension](#findextension)|Ta funkcja jest przeciążony element otoki dla [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587).|  
|[ATLPath::FindFileName](#findfilename)|Ta funkcja jest przeciążony element otoki dla [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589).|  
|[ATLPath::GetDriveNumber](#getdrivenumber)|Ta funkcja jest przeciążony element otoki dla [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612).|  
|[ATLPath::IsDirectory](#isdirectory)|Ta funkcja jest przeciążony element otoki dla [PathIsDirectory](http://msdn.microsoft.com/library/windows/desktop/bb773621).|  
|[ATLPath::IsFileSpec](#isfilespec)|Ta funkcja jest przeciążony element otoki dla [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627).|  
|[ATLPath::IsPrefix](#isprefix)|Ta funkcja jest przeciążony element otoki dla [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650).|  
|[ATLPath::IsRelative](#isrelative)|Ta funkcja jest przeciążony element otoki dla [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660).|  
|[ATLPath::IsRoot](#isroot)|Ta funkcja jest przeciążony element otoki dla [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674).|  
|[ATLPath::IsSameRoot](#issameroot)|Ta funkcja jest przeciążony element otoki dla [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687).|  
|[ATLPath::IsUNC](#isunc)|Ta funkcja jest przeciążony element otoki dla [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712).|  
|[ATLPath::IsUNCServer](#isuncserver)|Ta funkcja jest przeciążony element otoki dla [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722).|  
|[ATLPath::IsUNCServerShare](#isuncservershare)|Ta funkcja jest przeciążony element otoki dla [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723).|  
|[ATLPath::MakePretty](#makepretty)|Ta funkcja jest przeciążony element otoki dla [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725).|  
|[ATLPath::MatchSpec](#matchspec)|Ta funkcja jest przeciążony element otoki dla [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727).|  
|[ATLPath::QuoteSpaces](#quotespaces)|Ta funkcja jest przeciążony element otoki dla [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739).|  
|[ATLPath::RelativePathTo](#relativepathto)|Ta funkcja jest przeciążony element otoki dla [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740).|  
|[ATLPath::RemoveArgs](#removeargs)|Ta funkcja jest przeciążony element otoki dla [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742).|  
|[ATLPath::RemoveBackslash](#removebackslash)|Ta funkcja jest przeciążony element otoki dla [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743).|  
|[ATLPath::RemoveBlanks](#removeblanks)|Ta funkcja jest przeciążony element otoki dla [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745).|  
|[ATLPath::RemoveExtension](#removeextension)|Ta funkcja jest przeciążony element otoki dla [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746).|  
|[ATLPath::RemoveFileSpec](#removefilespec)|Ta funkcja jest przeciążony element otoki dla [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748).|  
|[ATLPath::RenameExtension](#renameextension)|Ta funkcja jest przeciążony element otoki dla [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749).|  
|[ATLPath::SkipRoot](#skiproot)|Ta funkcja jest przeciążony element otoki dla [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754).|  
|[ATLPath::StripPath](#strippath)|Ta funkcja jest przeciążony element otoki dla [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756).|  
|[ATLPath::StripToRoot](#striptoroot)|Ta funkcja jest przeciążony element otoki dla [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757).|  
|[ATLPath::UnquoteSpaces](#unquotespaces)|Ta funkcja jest przeciążony element otoki dla [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763).|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlpath.h  

## <a name="addbackslash"></a> ATLPath::AddBackSlash

Ta funkcja jest przeciążony element otoki dla [PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline char* AddBackslash(char* pszPath);  
inline wchar_t* AddBackslash(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561) szczegółowe informacje.  
  
 
  

## <a name="addextension"></a> ATLPath::AddExtension
 Ta funkcja jest przeciążony element otoki dla [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline BOOL AddExtension(char* pszPath, const char* pszExtension);  
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563) szczegółowe informacje. 
  
## <a name="append"></a> ATLPath::Append
 Ta funkcja jest przeciążony element otoki dla [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline BOOL Append(char* pszPath, const char* pszMore);  
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565) szczegółowe informacje.  
  
 
  

## <a name="buildroot"></a> ATLPath::BuildRoot
 Ta funkcja jest przeciążony element otoki dla [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline char* BuildRoot(char* pszPath, int iDrive);  
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567) szczegółowe informacje.  
  
 
  

## <a name="canonicalize"></a> ATLPath::Canonicalize
 Ta funkcja jest przeciążony element otoki dla [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);  
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569) szczegółowe informacje.  
  
 
  

## <a name="combine"></a> ATLPath::Combine 
Ta funkcja jest przeciążony element otoki dla [PathCombine](https://msdn.microsoft.com/en-us/library/windows/desktop/bb773571).  

### <a name="syntax"></a>Składnia  
```
inline char* Combine(  
   char* pszDest,
   const char* pszDir,
   const char* pszFile 
);

inline wchar_t* Combine(  
   wchar_t* pszDest,
   const wchar_t* pszDir,
   const wchar_t* pszFile);
```
### <a name="remarks"></a>Uwagi
Aby uzyskać więcej informacji, zobacz PathCombine.


## <a name="commonprefix">ATLPath::CommonPrefix</a>
 Ta funkcja jest przeciążony element otoki dla [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline int CommonPrefix(  
   const char* pszFile1, 
   const char* pszFile2,  
   char* pszDest);  

inline int CommonPrefix(  
   const wchar_t* pszFile1,  
   const wchar_t* pszFile2,  
   wchar_t* pszDest);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574) szczegółowe informacje.  
  
 
  

## <a name="compactpath"></a> ATLPath::CompactPath
 Ta funkcja jest przeciążony element otoki dla [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline BOOL CompactPath(  
   HDC hDC,  
   char* pszPath,  
   UINT dx);  

inline BOOL CompactPath(  
   HDC hDC,  
   wchar_t* pszPath,  
   UINT dx);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575) szczegółowe informacje.  
  
 
  

## <a name="compactpathex"></a> ATLPath::CompactPathEx
 Ta funkcja jest przeciążony element otoki dla [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline BOOL CompactPathEx(  
   char* pszDest,  
   const char* pszSrc,  
   UINT nMaxChars,  
   DWORD dwFlags);  

inline BOOL CompactPathEx(  
   wchar_t* pszDest,  
   const wchar_t* pszSrc,  
   UINT nMaxChars,  
   DWORD dwFlags);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578) szczegółowe informacje.  
  
 
  

## <a name="fileexists"></a> ATLPath::FileExists
 Ta funkcja jest przeciążony element otoki dla [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline BOOL FileExists(const char* pszPath);  
inline BOOL FileExists(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584) szczegółowe informacje.  
  
 
  

## <a name="findextension"></a> ATLPath::FindExtension
 Ta funkcja jest przeciążony element otoki dla [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline char* FindExtension(const char* pszPath);  
inline wchar_t* FindExtension(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587) szczegółowe informacje.  
  
 
  

## <a name="findfilename"></a> ATLPath::FindFileName
 Ta funkcja jest przeciążony element otoki dla [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline char* FindFileName(const char* pszPath);  
inline wchar_t* FindFileName(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589) szczegółowe informacje.  
  
 
  

## <a name="getdrivenumber"></a> ATLPath::GetDriveNumber  
 Ta funkcja jest przeciążony element otoki dla [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline int GetDriveNumber(const char* pszPath);  
inline int GetDriveNumber(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612) szczegółowe informacje.  
  
 


## <a name="isdirectory"></a>  ATLPath::IsDirectory 
Ta funkcja jest przeciążony element otoki dla [PathIsDirectory](https://msdn.microsoft.com/en-us/library/windows/desktop/bb773621).

```  
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```  
### <a name="remarks"></a>Uwagi
Aby uzyskać więcej informacji, zobacz PathIsDirectory.  

## <a name="isfilespec"></a> ATLPath::IsFileSpec
 Ta funkcja jest przeciążony element otoki dla [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline BOOL IsFileSpec(const char* pszPath);  
inline BOOL IsFileSpec(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627) szczegółowe informacje.  
  
 
  

## <a name="isprefix">ATLPath::IsPrefix</a>
 Ta funkcja jest przeciążony element otoki dla [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);  
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650) szczegółowe informacje.  
  
 
  

## <a name="isrelative"></a> ATLPath::IsRelative
 Ta funkcja jest przeciążony element otoki dla [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline BOOL IsRelative(const char* pszPath);  
inline BOOL IsRelative(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660) szczegółowe informacje.  
  
 
  

## <a name="isroot"></a> ATLPath::IsRoot
 Ta funkcja jest przeciążony element otoki dla [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline BOOL IsRoot(const char* pszPath);  
inline BOOL IsRoot(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674) szczegółowe informacje.  
  
 
  

## <a name="issameroot"></a> ATLPath::IsSameRoot
 Ta funkcja jest przeciążony element otoki dla [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);  
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687) szczegółowe informacje.  
  
 
  

## <a name="isunc"></a> ATLPath::IsUNC
 Ta funkcja jest przeciążony element otoki dla [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline BOOL IsUNC(const char* pszPath);  
inline BOOL IsUNC(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712) szczegółowe informacje.  
  
 
  

## <a name="isuncserver"></a> ATLPath::IsUNCServer
 Ta funkcja jest przeciążony element otoki dla [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline BOOL IsUNCServer(const char* pszPath);  
inline BOOL IsUNCServer(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722) szczegółowe informacje.  
  
 
  

## <a name="isuncservershare"></a> ATLPath::IsUNCServerShare
 Ta funkcja jest przeciążony element otoki dla [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline BOOL IsUNCServerShare(const char* pszPath);  
inline BOOL IsUNCServerShare(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723) szczegółowe informacje.  
  
 
  

## <a name="makepretty"></a> ATLPath::MakePretty
 Ta funkcja jest przeciążony element otoki dla [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline BOOL MakePretty(char* pszPath);  
inline BOOL MakePretty(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725) szczegółowe informacje.  
  
 
  

## <a name="matchspec"></a> ATLPath::MatchSpec  
 Ta funkcja jest przeciążony element otoki dla [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);  
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727) szczegółowe informacje.  
  
 
  

## <a name="quotespaces"></a> ATLPath::QuoteSpaces  
 Ta funkcja jest przeciążony element otoki dla [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline void QuoteSpaces(char* pszPath);  
inline void QuoteSpaces(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739) szczegółowe informacje.  
  
 
  

## <a name="relativepathto"></a> ATLPath::RelativePathTo
 Ta funkcja jest przeciążony element otoki dla [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline BOOL RelativePathTo(  
   char* pszPath,  
   const char* pszFrom,  
   DWORD dwAttrFrom,  
   const char* pszTo,  
   DWORD dwAttrTo);  

inline BOOL RelativePathTo(  
   wchar_t* pszPath,  
   const wchar_t* pszFrom,  
   DWORD dwAttrFrom,  
   const wchar_t* pszTo,  
   DWORD dwAttrTo);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740) szczegółowe informacje.  
  
 
  

## <a name="removeargs"></a> ATLPath::RemoveArgs  
 Ta funkcja jest przeciążony element otoki dla [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline void RemoveArgs(char* pszPath);  
inline void RemoveArgs(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742) szczegółowe informacje.  
  
 
  

## <a name="removebackslash"></a> ATLPath::RemoveBackslash
 Ta funkcja jest przeciążony element otoki dla [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline char* RemoveBackslash(char* pszPath);  
inline wchar_t* RemoveBackslash(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743) szczegółowe informacje.  
  
 
  

## <a name="removeblanks"></a> ATLPath::RemoveBlanks
 Ta funkcja jest przeciążony element otoki dla [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline void RemoveBlanks(char* pszPath);  
inline void RemoveBlanks(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745) szczegółowe informacje.  
  
 
  

## <a name="removeextension"></a> ATLPath::RemoveExtension
 Ta funkcja jest przeciążony element otoki dla [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline void RemoveExtension(char* pszPath);  
inline void RemoveExtension(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746) szczegółowe informacje.  
  
 
  

## <a name="removefilespec"></a> ATLPath::RemoveFileSpec
 Ta funkcja jest przeciążony element otoki dla [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline BOOL RemoveFileSpec(char* pszPath);  
inline BOOL RemoveFileSpec(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748) szczegółowe informacje.  
  
 
  

## <a name="renameextension"></a> ATLPath::RenameExtension
 Ta funkcja jest przeciążony element otoki dla [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline BOOL RenameExtension(char* pszPath, const char* pszExt);  
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749) szczegółowe informacje.  
  
 
  

## <a name="skiproot"></a> ATLPath::SkipRoot
 Ta funkcja jest przeciążony element otoki dla [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline char* SkipRoot(const char* pszPath);  
inline wchar_t* SkipRoot(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754) szczegółowe informacje.  
  
 
  

## <a name="strippath"></a> ATLPath::StripPath
 Ta funkcja jest przeciążony element otoki dla [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline void StripPath(char* pszPath);  
inline void StripPath(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756) szczegółowe informacje.  
  
 
  


## <a name="striptoroot"></a> ATLPath::StripToRoot
 Ta funkcja jest przeciążony element otoki dla [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline BOOL StripToRoot(char* pszPath);  
inline BOOL StripToRoot(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757) szczegółowe informacje.  
  
 
  

## <a name="unquotespaces"></a> ATLPath::UnquoteSpaces
 Ta funkcja jest przeciążony element otoki dla [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763).  
  
### <a name="syntax"></a>Składnia  
  
```  
inline void UnquoteSpaces(char* pszPath);  
inline void UnquoteSpaces(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763) szczegółowe informacje.  
  
 
  
 
