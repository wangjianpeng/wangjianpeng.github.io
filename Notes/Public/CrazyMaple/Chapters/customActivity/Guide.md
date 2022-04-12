## 自定义活动前端接入指南
### 解析活动类型数据
```
Assets/BP/Lua/UI/GameActivities/CustomBanner/UICustomBannerMgr.lua.txt

-拉取自定义活动数据后，解析指定活动额数据
function M.cacheActivityData(responseJson)
    if M.mHadResponseData then
        return
    end
    M.mPreDataResponse = responseJson
    if responseJson.data and responseJson.data.activity_list and #responseJson.data.activity_list then
        for j, k in pairs(responseJson.data.activity_list) do
            if k and k.type  then
                if k.type==9 then
                    M.mOldBookActivityId = k.activity_id
                end
                M.setconfigByType(k.type,k.related_config,k.jump_page)
                ....
                --书籍投票
                M.CheckBookVote(k)
                ....
                M.xxxxFeature(k)
```

### 添加活动入口是否需要显示相关的提示红点
```
Assets/BP/Lua/UI/GameActivities/CustomBanner/UICustomBannerMgr.lua.txt

--检查每隔自定义活动数据对应的小红点提示
function M.checkRedCircleWithDataItem(data)
        ....
        elseif type == 24 then
            canshow = require("BookVoteMgr").IsShowRedPoint()
        else 
            --这里有新的类型
            --比如13 插屏广告活动类型,14 活动时间管理的类型
            --如果是新加的活动类型，需要展示在banner上，没有其他特别的红点提示 ，不用在这个方法添加；如果是有特殊的红点处理逻辑，需要自行处理
            if not M.isUnShownBanner(type) then
                canshow = M.hasAddEnterRecord(bannerId)    
            end
        end
    end
    return canshow
end        
```

```
hasAddEnterRecord(bannerId)

这个方法是判定玩家有没有点击过banner，对于普通banner，从没有点击，需要显示红点；点击过就不再显示红点；其他特别的banner需要自行处理。
```

### 添加banner 红点的提示逻辑

```
Assets/BP/Lua/UI/GameActivities/CustomBanner/UICustomBanner.lua.txt

--判断是否显示小红点
--如果节点隐藏，那么就不会处理这个节点
function M:hasRedCircle()
    ...
    if self.mBannerType == 24 then
        if not show then
            show  = require("BookVoteMgr").IsShowRedPoint()
        end
    end
    --如果是新加的活动类型，需要展示在banner上，没有其他特别的红点提示 ，不用在这个方法添加；如果是有特殊的红点处理逻辑，需要自行处理
    return show    
```

### 添加banner的点击逻辑

```
Assets/BP/Lua/UI/GameActivities/CustomBanner/UICustomBanner.lua.txt

--点击banner
function M:onClickHandler()
    ...
            elseif type == 24 then
                local bvMgr = require("BookVoteMgr")
                bvMgr.OpenVoteDetail(3,2)
            --新加的活动类型，需要在此处添加对应的点击事件
	        end
        end
    end
    if self.mBannerType and self.mActivityId then
        WLog('click banner  id :'..self.mBannerType..' and the activity id : '..self.mActivityId..' the gameobj name :'..tostring(self.mGo.name))
    end
end  
```

### banner界面修改

```
Assets/BP/Lua/UI/GameActivities/CustomBanner/UICustomBanner.lua.txt

--刷新界面
function M:refreshBanner(index)
    ...
            elseif self.mBannerType == 24 then
                local str =CS.CommonTools.GetLocalString("BookVote/Vote", "Vote")
                CSUtil.SetText(self.mBtnText,str)
                customBannerMgr.setBtnIg(self.mGo,false)
                CSUtil.SetActive(self.mBtnText, true)
                CSUtil.SetActive(self.mGoBtn, true)
            -- 如果要订制专门的样式，需要在这里针对对应的活动类型添加对应的修改。
            end
            index = self.mActivityFrame:SetItemPos(self.mRectTran, index)
            self:checkDownloadTexture()
        end
    else
        CSUtil.SetActive(self.mGo,false)
    end
    --Util.wlog('refresh banner with '..self.mGo.name..' and the state is '..tostring(self.mGo.activeSelf)..' and index id '..tostring(index)
    --        .."; activity id:"..tostring(M.mActivityId))
    return index
end
```
