--Variable
lastPres = nil
loadDone = false

function onLoad()
	loadDone = true
end

function onDrop(playerColor)
	local options = Global.getTable('options')
	Global.call('moveObjectToPlayerByGUID', {guid = self.getGUID(), forward = 11, height = 2.2, max = 18})
	if options.scriptedVoting then
		local currentPres = Global.call('getPres')
		if lastPres ~= currentPres then
			Global.setVar('disableVote', false)
			Global.setVar('votePassed', false)
			Global.call('returnVoteCardsToHand')
		end
		lastPres = currentPres
	end
end

function onCollisionEnter(collisionInfo)
	if collisionInfo and loadDone then
		local options = Global.getTable('options')
		if options.autoNotate then
			local notate = Global.getTable('notate')
			if notate.line and notate.action == 'gives pres to' then
				Global.call('notateColor2ByObject', {self})
			end
		end
	end
end