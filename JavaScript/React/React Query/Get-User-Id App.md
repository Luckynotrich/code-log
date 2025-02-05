```js
import React, { useState, useEffect, useContext } from "react";
import axios from "axios";

import {useQuery} from "@tanstack/react-query";

import Main from "./components/main.jsx";
import "./scss/App.scss";

const GetUserId = async () => {
	const response = await axios.get("/getId");//http://localhost:8081
	return await response.data;
};

export default function App() {
	const {
		data: ID,
		isLoading,
		isError,
		error,
		onSuccess,
	} = useQuery({
		queryKey: ["ID"],
		queryFn: async () => await GetUserId(),
		staleTime: 60 * 60 * 1000,
		cacheTime: 1000 * 60 * 60,
	});
if
if(ID){
	return <Main UserId={ID}></Main>;
	}
}


```