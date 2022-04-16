<script>
  import Card from "./Card.svelte";

  const getSchemaForGame = async () => {
    const achievements = await fetch("https://api.steampowered.com/ISteamUserStats/GetSchemaForGame/v2/?key=STEAM_API_KEY&appid=APPID&l=LANGUAGE", {
      method: "get",
      responseType: "json",
    });
    const achievementsJson = await achievements.json();
    return achievementsJson.game.availableGameStats.achievements;
  };

  const getPlayerAchievements = async (STEAM_ID) => {
    const achievements = await fetch("https://api.steampowered.com/ISteamUserStats/GetPlayerAchievements/v1/?key=STEAM_API_KEY&steamid=STEAM_ID&appid=APPID", {
      method: "get",
      responseType: "json",
    });
    const achievementsJson = await achievements.json();
    return achievementsJson;
  };
</script>

<main>
  <div class="container" style="display: flex; flex-wrap: wrap">
    {#await getSchemaForGame() then schema}
      {#each schema as achievement}
        <Card icon={achievement.icon} title={achievement.displayName} description={achievement.description} />
      {/each}
    {/await}
  </div>
</main>
