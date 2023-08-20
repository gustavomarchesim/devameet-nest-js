- [] Válidar se existe um objeto ou não na próxima posição.
    1. getMeetObjects = retorna os objetos na sala

            async getMeetObjects(meetId:string, userId:string){
        this.logger.debug(`getMeetObjects - ${userId} - ${meetId}`);
        const user = await this.userService.getUserById(userId);
        const meet = await this.model.findOne({user, _id: meetId});

        return await this.objectModel.find({meet});
    }

    2. listUsersPositionByLink = lista a posição dos usuários na sala

            async listUsersPositionByLink(link: string){
        this.logger.debug(`listUsersPositionByLink - ${link}`);
        const meet = await this._getMeet(link);    
        return await this.positionModel.find({meet});
    }