# method
文字记录笔记

NSRange range = NSMakeRange(0, newArray.count);
NSIndexSet *set = [NSIndexSet indexSetWithIndexesInRange:range];
[array insertObjects:newArray atIndexes:set];

插入到数组的最前面