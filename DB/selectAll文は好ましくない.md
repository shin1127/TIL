# select * 文は好ましくない
DBの設計変更などで列が変化すると、検索結果も変化する→不具合のもと    
従って、`*`ではなくカラム名で表記したほうがよい
